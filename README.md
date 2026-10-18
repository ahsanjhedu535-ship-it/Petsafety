# PetSafetyHub — Next.js website project

PetSafetyHub is a responsive, multi-page Next.js website starter with a cream / terracotta / forest-green visual system. It includes the homepage, Dogs, Cats, Birds and Small Pets directories, 32 pet profile routes, blog listing and article pages, search, About, Contact, Privacy Policy and Terms pages, sitemap/robots metadata, and contact/newsletter API routes.

## Important launch checklist

- **Images:** profile and category photos currently use remote Unsplash image URLs, centrally defined in `lib/data.ts`. These are placeholders, not custom AI-generated breed images. For a requirement of 32 original AI images, generate and add one appropriately licensed image for every profile, save them under `public/images/`, then update the URLs in `lib/data.ts` before launch. The website does not claim these remote images are AI-generated.
- **Forms:** contact messages and newsletter signups are stored only when Supabase is configured. Without credentials, the API returns a clear setup message instead of pretending that data was saved.
- **Legal pages:** Privacy Policy and Terms are starter templates, not legal advice. Replace/update them for the actual operator, jurisdiction, analytics, advertising, retention, and third-party services.
- **Content:** care content is introductory educational information, not veterinary advice. Have a qualified source review medical or safety claims before publishing.
- **Ads:** no ad network is enabled by default. Add real Monetag/RevBid ad code only after account approval and policy review.
- **Production hardening:** before collecting real visitor data, add rate limiting/spam prevention, consent and retention practices, and test the forms with non-sensitive test records.

## Run locally

Requirements: Node.js 20 or newer.

```bash
npm install
npm run dev
```

Open `http://localhost:3000`.

## Check the project

```bash
npm run typecheck
npm run lint
npm run build
```

Run all three checks in an environment with dependencies installed before deploying. This environment could not complete `npm install` because network/DNS access was unavailable, so a production build could not be verified here.

## Configure Supabase form storage

1. Create a Supabase project.
2. Run `supabase-schema.sql` in the Supabase SQL Editor.
3. Copy the project URL and server-side service-role key from Supabase settings.
4. Copy `.env.example` to `.env.local` and fill in `SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY`, and optionally `NEXT_PUBLIC_SITE_URL`.
5. Never expose the service-role key with a `NEXT_PUBLIC_` prefix.
6. Restart the dev server and test both forms. Confirm rows appear in the Supabase tables.

## Deploy to Vercel

1. Upload the project folder to a GitHub repository.
2. Import it into Vercel and select the **Next.js** framework preset.
3. Build command: `npm run build` (or Vercel default). Install command: `npm install` (or Vercel default). Output directory: leave blank/default.
4. Add `SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY`, and `NEXT_PUBLIC_SITE_URL` in Vercel → Settings → Environment Variables as applicable.
5. Deploy and test each page, all profile links, search, forms, mobile navigation and sitemap.
6. Add your domain in Vercel → Settings → Domains, then apply the exact DNS records Vercel shows at your domain registrar.

## Routes

- `/`
- `/dogs`, `/cats`, `/birds`, `/small-pets`
- `/breeds/[slug]` (32 profile routes)
- `/blog`, `/blog/[slug]`
- `/search`, `/about`, `/contact`, `/privacy-policy`, `/terms`
- `/api/contact`, `/api/newsletter`
- `/sitemap.xml`, `/robots.txt`

## Local breed image assets
The 32 breed/species profile images are included locally under `public/images/breeds/` and referenced by each profile slug, so profile cards do not depend on third-party image URLs. These are AI-concept image crops prepared from the PetSafetyHub visual mockup and enlarged for the UI; they are not 32 separately generated, full-resolution source photographs. For a polished production launch, replace them with dedicated high-resolution AI-generated images if image sharpness is important.

