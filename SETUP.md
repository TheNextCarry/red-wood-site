# TNC Inventory — free team setup

This is the shared version. Your team logs in from any computer. Marking a bag sold is saved in the cloud, not only on one laptop.

Cost: $0 on the free plans below.

## 1. Create a free Supabase project

1. Go to https://supabase.com and sign up.
2. Click **New project**.
3. Name it `tnc-inventory`. Choose any region close to you.
4. Set a database password and save it somewhere safe.
5. Wait until the project is ready (about 1–2 minutes).

## 2. Get two keys

In Supabase: **Project Settings → API**

Copy:

- **Project URL** (looks like `https://xxxx.supabase.co`)
- **anon public** key (long token)

You will paste these into the app.

## 3. Create the tables

1. In Supabase open **SQL Editor**.
2. Click **New query**.
3. Paste the entire contents of `schema.sql` from this folder.
4. Click **Run**.
5. You should see the 63 bags in **Table Editor → products**.

## 4. Turn on email login

1. **Authentication → Providers → Email**
2. Keep Email enabled.
3. For a small team, turn **off** “Confirm email” so teammates can sign in immediately (optional but easier).

## 5. Create your owner account

1. Open `index.html` locally or after you publish it.
2. Paste the Project URL and anon key on the setup screen.
3. Create your account with **your** email.
4. You are the owner.

Then invite the team: they open the same website, click Create account, and use their own emails.

## 6. Publish for free (so the team does not need the zip)

### Cloudflare Pages (recommended)

1. Go to https://pages.cloudflare.com and sign up free.
2. **Create** → **Upload assets**.
3. Upload this whole `tnc-cloud` folder.
4. Cloudflare gives you a link like `https://tnc-inventory.pages.dev`.
5. Send that link to the team.

Photos in the `images` folder will load on the website. The spreadsheet image URLs are also used as backup.


## Add bags yourself (do not wait on Grok)

In the app click **Add bag**. Fill SKU, brand, name, Landed, TNC, status (**On Order** is included), and attach a photo. Save. The team sees it immediately.

Photos go to a Supabase folder named `bags`. Cloudflare only hosts the website; you do not upload new bags there.

If you already ran the first schema, also run `patch-on-order.sql` once so **On Order** and photo upload work.

## Roles

- **Owner** — you. Can change status and notes.
- **Sales** — can mark reserved / sold and add notes.
- **Viewer** — look only (you can change roles later in the `profiles` table).

On the free plan, a project may pause if nobody opens it for 7 days. Opening the site once wakes it back up.
