# SKILL: Enterprise-Grade Site Generator

> **AI Context File** — Generate production-ready, enterprise-grade websites with full GDPR compliance, testing, monitoring, and modern best practices.
>
> **Trigger Prompt:** _"Using docs/skill-site-generator.md, create a new enterprise-grade website."_

---

## 📋 Table of Contents

1. [When to Use](#when-to-use)
2. [Enterprise Tech Stack](#enterprise-tech-stack)
3. [Interactive Questionnaire](#interactive-questionnaire)
4. [GDPR & Compliance](#gdpr--compliance)
5. [Site Types & Features](#site-types--features)
6. [Implementation Workflow](#implementation-workflow)
7. [Testing Strategy](#testing-strategy)
8. [Performance Optimization](#performance-optimization)
9. [Security Best Practices](#security-best-practices)
10. [Advanced SEO](#advanced-seo)
11. [Monitoring & Analytics](#monitoring--analytics)
12. [Accessibility (WCAG 2.1 AA)](#accessibility-wcag-21-aa)
13. [CI/CD Pipeline](#cicd-pipeline)
14. [Progressive Web App](#progressive-web-app)
15. [Code Templates & Patterns](#code-templates--patterns)
16. [Quality Checklist](#quality-checklist)

---

## When to Use

Use this skill when:

- Creating enterprise-grade production websites
- Building GDPR-compliant applications
- Implementing comprehensive testing strategies
- Setting up monitoring and analytics
- Following 2025 industry best practices
- Building scalable, maintainable applications

---

## Enterprise Tech Stack

| Layer          | Technology               | Version | Purpose                            |
| -------------- | ------------------------ | ------- | ---------------------------------- |
| **Framework**  | React Router 7           | Latest  | SSR, routing, loaders/actions      |
| **Database**   | PostgreSQL + Prisma      | 6.x     | ORM, migrations, type-safe queries |
| **Styling**    | Tailwind CSS + shadcn/ui | 4.x     | Utility-first, component library   |
| **Validation** | Zod                      | 3.x     | Runtime type validation            |
| **i18n**       | react-i18next            | Latest  | Internationalization               |
| **Theme**      | next-themes              | Latest  | Dark/light mode                    |
| **Auth**       | secure-auth-sdk          | Custom  | OWASP ASVS Level 2 compliant       |
| **Linting**    | Biome                    | 1.x     | Fast linter/formatter              |
| **Testing**    | Vitest + Playwright      | Latest  | Unit + E2E testing                 |
| **Monitoring** | Sentry                   | Latest  | Error tracking, performance        |
| **Analytics**  | Plausible/GA4            | Latest  | Privacy-first analytics            |
| **Email**      | Resend                   | Latest  | Transactional emails               |
| **Storage**    | Supabase Storage         | Latest  | CDN, file uploads                  |
| **Payments**   | Stripe                   | Latest  | Payment processing                 |
| **Language**   | TypeScript               | 5.x     | Type safety                        |

### Enterprise Project Structure

```
app/
├── routes/                    # Route files (meta/loader/action only)
│   ├── $lang/                 # Language-prefixed routes
│   └── api/                   # API endpoints
├── components/
│   ├── pages/                 # Page components (logic + UI)
│   ├── ui/                    # shadcn/ui components
│   ├── legal/                 # GDPR components (banner, policies)
│   └── custom/                # Custom enterprise components
├── lib/
│   ├── prisma.ts              # Prisma singleton
│   ├── sdk-auth.server.ts     # Auth adapter
│   ├── email.ts               # Email service
│   ├── monitoring/            # Sentry, analytics
│   ├── cache/                 # Redis caching
│   ├── services/              # Business logic
│   └── utils/                 # Helper functions
├── styles/                    # Global styles
├── locales/
│   ├── en/                    # English translations
│   └── it/                    # Italian translations
└── middleware/                # Request middleware

prisma/
├── schema.prisma              # Database schema
├── seed.ts                    # Database seed
└── migrations/                # Schema migrations

tests/
├── unit/                      # Vitest unit tests
├── e2e/                       # Playwright E2E tests
└── __mocks__/                 # Test mocks

scripts/
├── test-e2e.ts                # E2E test runner
├── seed-db.ts                 # Database seeding
└── migrate.ts                 # Migration helper

.github/
└── workflows/                 # CI/CD pipelines

public/
├── locales/                   # Client-side translations
├── robots.txt                 # SEO robots
├── sitemap.xml                # SEO sitemap
└── sw.js                      # Service worker (PWA)
```

---

## Interactive Questionnaire

### Phase 1: Core Requirements (Always Ask)

#### 1. Site Type

```
What type of enterprise website?

Options:
1. 🏢 Corporate - Company presence, compliance-heavy
2. 🛒 E-commerce - Online store with full payment flow
3. 📝 Blog - Content platform with advanced SEO
4. 💼 Portfolio - Professional showcase
5. 🏪 Showcase - Product/service display
6. 🏥 SaaS - Subscription-based service
7. ✨ Custom - Describe requirements
```

#### 2. Legal & Compliance

```
GDPR & Privacy Compliance:

Which regulations apply?
✅ GDPR (EU)
✅ CCPA (California)
✅ LGPD (Brazil)
✅ PDPB (India)
✅ None/Other

Required features:
✅ Cookie consent banner
✅ Privacy policy page
✅ Cookie policy page
✅ Terms of service page
✅ Data deletion requests
✅ Right to access/export
✅ Cookie preferences management
```

#### 3. Authentication Strategy

```
User Authentication:

Authentication type:
1. 🔐 Email/Password (secure-auth-sdk)
2. 🔑 Magic Link (passwordless)
3. 🌐 Social Login (Google, GitHub, etc.)
4. 🔑 SSO (SAML, LDAP)
5. 👥 Multi-factor (TOTP)

User roles:
• Admin (full access)
• Manager (limited admin)
• Customer (user account)
• Custom roles

Session management:
• Browser sessions only
• Remember me (30 days)
• Multi-device support
• Session audit log
```

#### 4. Multi-language Strategy

```
Internationalization:

Supported languages:
• English (en) - Default
• Italian (it)
• Spanish (es)
• French (fr)
• German (de)
• Other: ______

URL strategy:
1. /en/page, /it/page (path prefix)
2. subdomain.domain.com
3. domain.com?lang=en

Content translation:
• Manual translation
• Machine translation (DeepL)
• Hybrid approach
```

#### 5. Design & Accessibility

```
Design Requirements:

Design style:
• Minimalist
• Corporate/Professional
• Bold/Creative
• Custom: ______

Accessibility level:
• WCAG 2.1 AA (recommended)
• WCAG 2.1 AAA (strict)
• Basic accessibility

Theme support:
• Light only
• Dark only
• Light/Dark toggle
• System preference

Design system:
• Use existing shadcn/ui
• Custom components
• Mixed approach
```

### Phase 2: Features (Site-Specific)

#### 6. E-commerce Features

```
For E-commerce sites:

Product management:
✅ Product catalog with categories
✅ Product variants (size, color)
✅ Inventory tracking
✅ Product reviews/ratings
✅ Product comparisons
✅ Wishlists

Shopping experience:
✅ Shopping cart (guest + user)
✅ Guest checkout
✅ Saved addresses
✅ Order tracking
✅ Multiple payment methods
✅ Discount codes

Payment processing:
✅ Stripe (credit cards)
✅ PayPal
✅ Apple Pay/Google Pay
✅ Bank transfer
✅ Cash on delivery

Fulfillment:
✅ Shipping calculation
✅ Tax calculation (VAT)
✅ Digital downloads
✅ Gift cards
✅ Pre-orders
```

#### 7. Content Features

```
For Blog/Content sites:

Content management:
✅ Rich text editor
✅ Markdown support
✅ Media library
✅ Categories/Tags
✅ Featured content
✅ Scheduled publishing
✅ Revision history

Engagement:
✅ Comments (moderated)
✅ Social sharing
✅ RSS feeds
✅ Newsletter signup
✅ Author profiles

SEO:
✅ Meta fields per post
✅ Open Graph tags
✅ Twitter Cards
✅ Schema.org markup
✅ Sitemap auto-update
```

#### 8. Enterprise Features

```
Advanced Features:

Analytics & Tracking:
✅ Google Analytics 4
✅ Plausible (privacy-first)
✅ Facebook Pixel
✅ LinkedIn Pixel
✅ Custom events

Performance:
✅ Image optimization
✅ Code splitting
✅ Lazy loading
✅ CDN integration
✅ Caching strategy
✅ Bundle analysis

Monitoring:
✅ Error tracking (Sentry)
✅ Performance monitoring
✅ Uptime monitoring
✅ User feedback
✅ A/B testing
```

### Phase 3: Technical Decisions

#### 9. Testing Requirements

```
Testing Strategy:

Unit testing:
✅ Critical business logic
✅ Utility functions
✅ Custom hooks
✅ API endpoints
Target coverage: 80%+

Integration testing:
✅ Database operations
✅ External APIs
✅ Payment flow
✅ Email sending

E2E testing:
✅ Critical user flows
✅ Checkout process
✅ Authentication
✅ Form submissions
```

#### 10. Deployment Strategy

```
Deployment & DevOps:

Hosting:
• Vercel (recommended)
• Netlify
• AWS/GCP/Azure
• Self-hosted

CI/CD:
✅ GitHub Actions
✅ Automated testing
✅ Staging environment
✅ Production deployment
✅ Rollback capability

Environment management:
✅ Development
✅ Staging
✅ Production
✅ Feature flags
```

---

## GDPR & Compliance

### Automatic GDPR Implementation

When you generate a site with this skill, the following compliance features are **automatically included**:

#### 1. Cookie Consent Banner

**Component**: `app/components/legal/CookieBanner.tsx`

```tsx
import { useState, useEffect } from "react";
import { useTranslation } from "react-i18next";
import { Button } from "~/components/ui/button";
import { Card } from "~/components/ui/card";

const CONSENT_KEY = "cookie_consent";

type ConsentPreferences = {
  necessary: boolean; // Always true (functional cookies)
  analytics: boolean; // Google Analytics, Plausible
  marketing: boolean; // Facebook Pixel, LinkedIn
  preferences: boolean; // Theme, language settings
};

export function CookieBanner() {
  const { t } = useTranslation();
  const [isVisible, setIsVisible] = useState(false);
  const [showPreferences, setShowPreferences] = useState(false);

  useEffect(() => {
    const consent = localStorage.getItem(CONSENT_KEY);
    if (!consent) {
      setIsVisible(true);
    } else {
      // Apply saved consent
      const preferences = JSON.parse(consent) as ConsentPreferences;
      applyConsent(preferences);
    }
  }, []);

  const applyConsent = (preferences: ConsentPreferences) => {
    // Initialize analytics if consented
    if (preferences.analytics) {
      window.gtag?.("consent", "update", {
        analytics_storage: "granted",
      });
    }

    // Initialize marketing if consented
    if (preferences.marketing) {
      window.gtag?.("consent", "update", {
        ad_storage: "granted",
        ad_user_data: "granted",
        ad_personalization: "granted",
      });
    }

    // Fire consent event for other scripts
    window.dispatchEvent(new CustomEvent("cookie-consent", { detail: preferences }));
  };

  const handleAcceptAll = () => {
    const preferences: ConsentPreferences = {
      necessary: true,
      analytics: true,
      marketing: true,
      preferences: true,
    };
    localStorage.setItem(CONSENT_KEY, JSON.stringify(preferences));
    applyConsent(preferences);
    setIsVisible(false);
  };

  const handleAcceptNecessary = () => {
    const preferences: ConsentPreferences = {
      necessary: true,
      analytics: false,
      marketing: false,
      preferences: false,
    };
    localStorage.setItem(CONSENT_KEY, JSON.stringify(preferences));
    applyConsent(preferences);
    setIsVisible(false);
  };

  const handleSavePreferences = (preferences: ConsentPreferences) => {
    localStorage.setItem(CONSENT_KEY, JSON.stringify(preferences));
    applyConsent(preferences);
    setIsVisible(false);
    setShowPreferences(false);
  };

  if (!isVisible) return null;

  return (
    <div className="fixed bottom-0 left-0 right-0 z-50 border-t bg-background p-4 shadow-lg">
      <div className="mx-auto max-w-7xl">
        <Card className="p-6">
          <div className="flex flex-col gap-4 md:flex-row md:items-center md:justify-between">
            <div className="flex-1">
              <h3 className="text-lg font-semibold">{t("cookieBanner.title")}</h3>
              <p className="mt-2 text-sm text-muted-foreground">{t("cookieBanner.description")}</p>
            </div>
            <div className="flex gap-3">
              <Button variant="outline" onClick={() => setShowPreferences(true)}>
                {t("cookieBanner.preferences")}
              </Button>
              <Button variant="ghost" onClick={handleAcceptNecessary}>
                {t("cookieBanner.acceptNecessary")}
              </Button>
              <Button onClick={handleAcceptAll}>{t("cookieBanner.acceptAll")}</Button>
            </div>
          </div>

          {showPreferences && <CookiePreferences onSave={handleSavePreferences} onClose={() => setShowPreferences(false)} />}
        </Card>
      </div>
    </div>
  );
}

function CookiePreferences({ onSave, onClose }: { onSave: (preferences: ConsentPreferences) => void; onClose: () => void }) {
  const { t } = useTranslation();
  const [preferences, setPreferences] = useState<ConsentPreferences>({
    necessary: true,
    analytics: false,
    marketing: false,
    preferences: false,
  });

  return (
    <div className="mt-6 space-y-4 border-t pt-6">
      <h4 className="font-semibold">{t("cookiePreferences.title")}</h4>

      <CookieToggle
        name="necessary"
        label={t("cookieCategories.necessary")}
        description={t("cookieCategories.necessaryDesc")}
        checked={preferences.necessary}
        disabled
      />

      <CookieToggle
        name="preferences"
        label={t("cookieCategories.preferences")}
        description={t("cookieCategories.preferencesDesc")}
        checked={preferences.preferences}
        onChange={(checked) => setPreferences({ ...preferences, preferences: checked })}
      />

      <CookieToggle
        name="analytics"
        label={t("cookieCategories.analytics")}
        description={t("cookieCategories.analyticsDesc")}
        checked={preferences.analytics}
        onChange={(checked) => setPreferences({ ...preferences, analytics: checked })}
      />

      <CookieToggle
        name="marketing"
        label={t("cookieCategories.marketing")}
        description={t("cookieCategories.marketingDesc")}
        checked={preferences.marketing}
        onChange={(checked) => setPreferences({ ...preferences, marketing: checked })}
      />

      <div className="flex justify-end gap-3">
        <Button variant="outline" onClick={onClose}>
          {t("cookiePreferences.cancel")}
        </Button>
        <Button onClick={() => onSave(preferences)}>{t("cookiePreferences.save")}</Button>
      </div>
    </div>
  );
}

function CookieToggle({
  name,
  label,
  description,
  checked,
  disabled = false,
  onChange,
}: {
  name: string;
  label: string;
  description: string;
  checked: boolean;
  disabled?: boolean;
  onChange?: (checked: boolean) => void;
}) {
  return (
    <div className="flex items-center justify-between rounded-lg border p-4">
      <div>
        <p className="font-medium">{label}</p>
        <p className="text-sm text-muted-foreground">{description}</p>
      </div>
      <input type="checkbox" id={name} checked={checked} disabled={disabled} onChange={(e) => onChange?.(e.target.checked)} className="h-5 w-5 rounded" />
    </div>
  );
}
```

#### 2. Privacy Policy Page

**Route**: `app/routes/$lang/privacy.tsx`

```tsx
import type { MetaFunction } from "react-router";
import { PrivacyPolicy } from "~/components/pages/PrivacyPolicy";

export const meta: MetaFunction = ({ params }) => {
  const lang = params.lang || "en";
  return [
    { title: `Privacy Policy | ${lang === "it" ? "Sito" : "Site"}` },
    { name: "description", content: "Our privacy policy and data protection practices" },
  ];
};

export default function PrivacyRoute() {
  return <PrivacyPolicy />;
}
```

**Component**: `app/components/pages/PrivacyPolicy.tsx`

```tsx
import { useTranslation } from "react-i18next";
import { Card, CardContent } from "~/components/ui/card";
import { ScrollAnimatedSection } from "~/components/storefront/ScrollAnimatedSection";

export function PrivacyPolicy() {
  const { t } = useTranslation();

  return (
    <div className="flex flex-col">
      <ScrollAnimatedSection sectionId="privacy-hero">
        <section className="bg-muted/50 py-20">
          <div className="mx-auto max-w-4xl px-6">
            <h1 className="text-4xl font-bold">{t("privacy.title")}</h1>
            <p className="mt-4 text-lg text-muted-foreground">{t("privacy.lastUpdated", { date: new Date().toLocaleDateString() })}</p>
          </div>
        </section>
      </ScrollAnimatedSection>

      <ScrollAnimatedSection sectionId="privacy-content">
        <section className="py-16">
          <div className="mx-auto max-w-4xl space-y-8 px-6">
            <Card>
              <CardContent className="space-y-6 p-8">
                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("privacy.sections.introduction.title")}</h2>
                  <div className="prose prose-slate max-w-none">
                    <p>{t("privacy.sections.introduction.content")}</p>
                  </div>
                </section>

                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("privacy.sections.dataCollection.title")}</h2>
                  <div className="space-y-4">
                    <h3 className="text-xl font-medium">{t("privacy.sections.dataCollection.personalData.title")}</h3>
                    <ul className="list-disc pl-6 space-y-2">
                      <li>{t("privacy.sections.dataCollection.personalData.items.name")}</li>
                      <li>{t("privacy.sections.dataCollection.personalData.items.email")}</li>
                      <li>{t("privacy.sections.dataCollection.personalData.items.address")}</li>
                      <li>{t("privacy.sections.dataCollection.personalData.items.phone")}</li>
                    </ul>
                  </div>
                </section>

                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("privacy.sections.dataUsage.title")}</h2>
                  <ul className="list-disc pl-6 space-y-2">
                    <li>{t("privacy.sections.dataUsage.items.orderProcessing")}</li>
                    <li>{t("privacy.sections.dataUsage.items.accountManagement")}</li>
                    <li>{t("privacy.sections.dataUsage.items.communications")}</li>
                    <li>{t("privacy.sections.dataUsage.items.analytics")}</li>
                  </ul>
                </section>

                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("privacy.sections.userRights.title")}</h2>
                  <div className="space-y-3">
                    <RightCard
                      title={t("privacy.sections.userRights.rights.access.title")}
                      description={t("privacy.sections.userRights.rights.access.description")}
                    />
                    <RightCard
                      title={t("privacy.sections.userRights.rights.rectification.title")}
                      description={t("privacy.sections.userRights.rights.rectification.description")}
                    />
                    <RightCard
                      title={t("privacy.sections.userRights.rights.erasure.title")}
                      description={t("privacy.sections.userRights.rights.erasure.description")}
                    />
                    <RightCard
                      title={t("privacy.sections.userRights.rights.portability.title")}
                      description={t("privacy.sections.userRights.rights.portability.description")}
                    />
                    <RightCard
                      title={t("privacy.sections.userRights.rights.objection.title")}
                      description={t("privacy.sections.userRights.rights.objection.description")}
                    />
                  </div>
                </section>

                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("privacy.sections.cookies.title")}</h2>
                  <p className="mb-4">{t("privacy.sections.cookies.description")}</p>
                  <a href={`/${useTranslation().i18n.language}/cookie-policy`} className="text-primary hover:underline">
                    {t("privacy.sections.cookies.viewPolicy")}
                  </a>
                </section>

                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("privacy.sections.contact.title")}</h2>
                  <p>{t("privacy.sections.contact.content")}</p>
                  <a href={`mailto:privacy@example.com`} className="text-primary hover:underline">
                    privacy@example.com
                  </a>
                </section>
              </CardContent>
            </Card>
          </div>
        </section>
      </ScrollAnimatedSection>
    </div>
  );
}

function RightCard({ title, description }: { title: string; description: string }) {
  return (
    <div className="rounded-lg border p-4">
      <h4 className="font-semibold">{title}</h4>
      <p className="mt-2 text-sm text-muted-foreground">{description}</p>
    </div>
  );
}
```

#### 3. Cookie Policy Page

**Route**: `app/routes/$lang/cookie-policy.tsx`

```tsx
import type { MetaFunction } from "react-router";
import { CookiePolicy } from "~/components/pages/CookiePolicy";

export const meta: MetaFunction = ({ params }) => {
  const lang = params.lang || "en";
  return [{ title: `Cookie Policy | ${lang === "it" ? "Sito" : "Site"}` }, { name: "description", content: "How we use cookies and your choices" }];
};

export default function CookiePolicyRoute() {
  return <CookiePolicy />;
}
```

**Component**: `app/components/pages/CookiePolicy.tsx`

```tsx
import { useTranslation } from "react-i18next";
import { Card, CardContent } from "~/components/ui/card";
import { ScrollAnimatedSection } from "~/components/storefront/ScrollAnimatedSection";

export function CookiePolicy() {
  const { t } = useTranslation();

  const cookieTypes = [
    {
      name: "Necessary",
      description: "Required for the site to function",
      examples: ["Authentication", "Shopping cart", "Security tokens"],
      alwaysOn: true,
    },
    {
      name: "Preferences",
      description: "Remember your settings",
      examples: ["Language", "Theme", "Layout preferences"],
      alwaysOn: false,
    },
    {
      name: "Analytics",
      description: "Help us improve the site",
      examples: ["Google Analytics", "Plausible", "Page view tracking"],
      alwaysOn: false,
    },
    {
      name: "Marketing",
      description: "For advertising and social media",
      examples: ["Facebook Pixel", "LinkedIn Insight", "Google Ads"],
      alwaysOn: false,
    },
  ];

  return (
    <div className="flex flex-col">
      <ScrollAnimatedSection sectionId="cookie-hero">
        <section className="bg-muted/50 py-20">
          <div className="mx-auto max-w-4xl px-6">
            <h1 className="text-4xl font-bold">{t("cookiePolicy.title")}</h1>
            <p className="mt-4 text-lg text-muted-foreground">{t("cookiePolicy.subtitle")}</p>
          </div>
        </section>
      </ScrollAnimatedSection>

      <ScrollAnimatedSection sectionId="cookie-content">
        <section className="py-16">
          <div className="mx-auto max-w-4xl space-y-8 px-6">
            <Card>
              <CardContent className="space-y-6 p-8">
                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("cookiePolicy.whatAreCookies")}</h2>
                  <p className="text-muted-foreground">{t("cookiePolicy.whatAreCookiesDesc")}</p>
                </section>

                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("cookiePolicy.howWeUseCookies")}</h2>
                  <div className="space-y-4">
                    {cookieTypes.map((type) => (
                      <div key={type.name} className="rounded-lg border p-4">
                        <div className="flex items-center justify-between">
                          <div>
                            <h3 className="font-semibold">{type.name}</h3>
                            <p className="mt-1 text-sm text-muted-foreground">{type.description}</p>
                            <ul className="mt-2 list-disc pl-6 text-sm">
                              {type.examples.map((example) => (
                                <li key={example}>{example}</li>
                              ))}
                            </ul>
                          </div>
                          {type.alwaysOn && <span className="rounded-full bg-primary px-3 py-1 text-xs text-primary-foreground">Always Active</span>}
                        </div>
                      </div>
                    ))}
                  </div>
                </section>

                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("cookiePolicy.managingCookies")}</h2>
                  <p className="mb-4 text-muted-foreground">{t("cookiePolicy.managingCookiesDesc")}</p>
                  <button
                    onClick={() => window.dispatchEvent(new Event("open-cookie-settings"))}
                    className="rounded-md bg-primary px-4 py-2 text-primary-foreground hover:bg-primary/90"
                  >
                    {t("cookiePolicy.updatePreferences")}
                  </button>
                </section>

                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("cookiePolicy.thirdPartyCookies")}</h2>
                  <ul className="list-disc pl-6 space-y-2 text-muted-foreground">
                    <li>
                      <strong>Google Analytics:</strong> {t("cookiePolicy.googleAnalytics")}
                    </li>
                    <li>
                      <strong>Stripe:</strong> {t("cookiePolicy.stripe")}
                    </li>
                    <li>
                      <strong>Resend:</strong> {t("cookiePolicy.resend")}
                    </li>
                  </ul>
                </section>

                <section>
                  <h2 className="mb-4 text-2xl font-semibold">{t("cookiePolicy.moreInfo")}</h2>
                  <a href={`mailto:privacy@example.com`} className="text-primary hover:underline">
                    privacy@example.com
                  </a>
                </section>
              </CardContent>
            </Card>
          </div>
        </section>
      </ScrollAnimatedSection>
    </div>
  );
}
```

#### 4. Terms of Service Page

**Route**: `app/routes/$lang/terms.tsx`

```tsx
import type { MetaFunction } from "react-router";
import { TermsOfService } from "~/components/pages/TermsOfService";

export const meta: MetaFunction = ({ params }) => {
  const lang = params.lang || "en";
  return [{ title: `Terms of Service | ${lang === "it" ? "Sito" : "Site"}` }, { name: "description", content: "Terms and conditions of use" }];
};

export default function TermsRoute() {
  return <TermsOfService />;
}
```

#### 5. Data Deletion API

**Route**: `app/routes/api/data-deletion.ts`

```tsx
import type { ActionFunctionArgs } from "react-router";
import { json, redirect } from "react-router";
import { prisma } from "~/lib/prisma";
import { requireUser } from "~/lib/sdk-auth.server";
import { sendDataDeletionEmail } from "~/lib/email";

export const action = async ({ request }: ActionFunctionArgs) => {
  const user = await requireUser(request);

  if (request.method !== "POST") {
    return json({ error: "Method not allowed" }, { status: 405 });
  }

  try {
    // GDPR: Right to be forgotten (Article 17)
    // 1. Delete user's personal data
    // 2. Anonymize orders and transactions
    // 3. Delete account and related data

    await prisma.$transaction(async (tx) => {
      // Anonymize orders (keep for legal/tax purposes)
      await tx.order.updateMany({
        where: { userId: user.id },
        data: {
          customerEmail: "deleted@anonymous",
          customerPhone: null,
          notes: "[GDPR DELETED]",
        },
      });

      // Delete addresses
      await tx.address.deleteMany({
        where: { userId: user.id },
      });

      // Delete cart
      await tx.cart.deleteMany({
        where: { userId: user.id },
      });

      // Delete wishlist
      await tx.wishlist.deleteMany({
        where: { userId: user.id },
      });

      // Delete sessions
      await tx.session.deleteMany({
        where: { userId: user.id },
      });

      // Delete auth tokens
      await tx.authEmailToken.deleteMany({
        where: { userId: user.id },
      });

      // Delete user
      await tx.user.delete({
        where: { id: user.id },
      });
    });

    // Send confirmation email
    await sendDataDeletionEmail(user.email, user.name || "User");

    return redirect("/data-deletion-confirmation");
  } catch (error) {
    console.error("Data deletion error:", error);
    return json({ error: "Failed to delete data. Please contact support." }, { status: 500 });
  }
};
```

#### 6. Data Export API

**Route**: `app/routes/api/data-export.ts`

```tsx
import type { LoaderFunctionArgs } from "react-router";
import { json } from "react-router";
import { prisma } from "~/lib/prisma";
import { requireUser } from "~/lib/sdk-auth.server";

// GDPR: Right to data portability (Article 20)
export const loader = async ({ request }: LoaderFunctionArgs) => {
  const user = await requireUser(request);

  try {
    // Collect all user data
    const [userData, orders, addresses, wishlist] = await Promise.all([
      prisma.user.findUnique({
        where: { id: user.id },
        select: {
          email: true,
          name: true,
          firstName: true,
          lastName: true,
          phone: true,
          createdAt: true,
          updatedAt: true,
        },
      }),
      prisma.order.findMany({
        where: { userId: user.id },
        orderBy: { createdAt: "desc" },
      }),
      prisma.address.findMany({
        where: { userId: user.id },
      }),
      prisma.wishlist.findUnique({
        where: { userId: user.id },
        include: { items: true },
      }),
    ]);

    const exportData = {
      personalData: userData,
      orders,
      addresses,
      wishlist,
      exportDate: new Date().toISOString(),
    };

    return json(exportData, {
      headers: {
        "Content-Disposition": `attachment; filename="data-export-${user.id}.json"`,
        "Content-Type": "application/json",
      },
    });
  } catch (error) {
    console.error("Data export error:", error);
    return json({ error: "Failed to export data. Please try again later." }, { status: 500 });
  }
};
```

#### 7. GDPR Translations

**Add to** `public/locales/en/common.json`:

```json
{
  "cookieBanner": {
    "title": "We value your privacy",
    "description": "We use cookies to enhance your experience. By continuing to visit this site you agree to our use of cookies.",
    "acceptAll": "Accept all",
    "acceptNecessary": "Accept necessary only",
    "preferences": "Customize"
  },
  "cookiePreferences": {
    "title": "Cookie Preferences",
    "save": "Save preferences",
    "cancel": "Cancel"
  },
  "cookieCategories": {
    "necessary": "Necessary",
    "necessaryDesc": "Required for the site to function properly",
    "preferences": "Preferences",
    "preferencesDesc": "Remember your settings and preferences",
    "analytics": "Analytics",
    "analyticsDesc": "Help us understand how you use our site",
    "marketing": "Marketing",
    "marketingDesc": "Track visitors across websites to display relevant ads"
  },
  "privacy": {
    "title": "Privacy Policy",
    "lastUpdated": "Last updated: {date}",
    "sections": {
      "introduction": {
        "title": "Introduction",
        "content": "This privacy policy explains how we collect, use, and protect your personal data in accordance with the GDPR."
      },
      "dataCollection": {
        "title": "Data We Collect",
        "personalData": {
          "title": "Personal Information",
          "items": {
            "name": "Name",
            "email": "Email address",
            "address": "Shipping/billing address",
            "phone": "Phone number"
          }
        }
      },
      "dataUsage": {
        "title": "How We Use Your Data",
        "items": {
          "orderProcessing": "Process and fulfill your orders",
          "accountManagement": "Manage your account",
          "communications": "Send you important updates",
          "analytics": "Improve our services"
        }
      },
      "userRights": {
        "title": "Your Rights Under GDPR",
        "rights": {
          "access": {
            "title": "Right to Access",
            "description": "You can request a copy of your personal data"
          },
          "rectification": {
            "title": "Right to Rectification",
            "description": "You can correct inaccurate or incomplete data"
          },
          "erasure": {
            "title": "Right to Erasure",
            "description": "You can request deletion of your personal data"
          },
          "portability": {
            "title": "Right to Portability",
            "description": "You can receive your data in a structured format"
          },
          "objection": {
            "title": "Right to Object",
            "description": "You can object to processing of your data"
          }
        }
      },
      "cookies": {
        "title": "Cookies",
        "description": "We use cookies to enhance your browsing experience. View our cookie policy for details.",
        "viewPolicy": "View Cookie Policy"
      },
      "contact": {
        "title": "Contact Us",
        "content": "For privacy-related inquiries, contact us at:"
      }
    }
  },
  "cookiePolicy": {
    "title": "Cookie Policy",
    "subtitle": "Understanding how we use cookies and your choices",
    "whatAreCookies": "What Are Cookies?",
    "whatAreCookiesDesc": "Cookies are small text files stored on your device when you visit our website. They help us provide you with a better experience.",
    "howWeUseCookies": "Types of Cookies We Use",
    "managingCookies": "Managing Your Cookie Preferences",
    "managingCookiesDesc": "You can manage your cookie preferences through our cookie banner. You can also manage cookies through your browser settings.",
    "updatePreferences": "Update Cookie Preferences",
    "thirdPartyCookies": "Third-Party Cookies",
    "googleAnalytics": "Analytics and user behavior tracking",
    "stripe": "Payment processing",
    "resend": "Email delivery and tracking",
    "moreInfo": "Need More Information?",
    "contact": "For questions about cookies, contact us at:"
  }
}
```

---

## Site Types & Features

### 1. Corporate Site (GDPR-Heavy)

**Compliance Features**:

- ✅ Cookie consent banner with granular controls
- ✅ Privacy policy (GDPR Article 13 & 14)
- ✅ Cookie policy
- ✅ Terms of service
- ✅ Data deletion API
- ✅ Data export API (GDPR Article 20)
- ✅ Right to access form
- ✅ Cookie preference management
- ✅ Consent logging

**Standard Pages**:

- Home
- About
- Services
- Case Studies
- Team
- Contact
- Privacy Policy
- Cookie Policy
- Terms of Service
- Data Request Portal

**Database Models**:

```prisma
model DataRequest {
  id          String   @id @default(cuid())
  type        String   // ACCESS, ERASURE, PORTABILITY, OBJECTION
  status      String   // PENDING, PROCESSING, COMPLETED, REJECTED
  userId      String
  email       String
  requestedAt DateTime @default(now())
  completedAt DateTime?
  notes       String?
  user        User     @relation(fields: [userId], references: [id])

  @@index([status])
  @@index([userId])
}

model ConsentLog {
  id          String   @id @default(cuid())
  userId      String?  // null for anonymous users
  consentType String   // COOKIE, PRIVACY, MARKETING
  action      String   // ACCEPTED, REVOKED, MODIFIED
  preferences Json     // Store consent preferences
  ipAddress   String
  userAgent   String
  timestamp   DateTime @default(now())

  @@index([userId])
  @@index([timestamp])
}
```

### 2. E-commerce Site

**Corporate Compliance** + **E-commerce Features**:

- ✅ All GDPR features
- ✅ Payment processing (PCI DSS compliance)
- ✅ VAT calculation (EU tax rules)
- ✅ Right of withdrawal (14 days for EU)
- ✅ Order confirmation emails
- ✅ Shipping confirmation
- ✅ Digital delivery for downloads

**Pages**:

- All corporate pages
- Products
- Product detail
- Cart
- Checkout
- Order confirmation
- Order tracking
- Account dashboard
- Right of withdrawal form

### 3. Blog/Content Site

**Features**:

- ✅ All GDPR features
- ✅ Author profiles
- ✅ Category management
- ✅ SEO optimization
- ✅ Social sharing (with consent)
- ✅ Newsletter signup (double opt-in)
- ✅ RSS feeds
- ✅ Comment moderation

---

## Implementation Workflow

### Phase 1: Planning & Requirements

**AI Actions**:

1. Collect requirements through questionnaire
2. Generate site architecture document
3. Create database schema plan
4. Plan GDPR compliance requirements
5. Design testing strategy

**Output**: `site-plan.md` with complete requirements

### Phase 2: Database Setup

**Steps**:

1. Update `prisma/schema.prisma`
2. Add GDPR compliance models (ConsentLog, DataRequest)
3. Create indexes for performance
4. Generate migration: `npx prisma migrate dev --name init_site`
5. Update `prisma/seed.ts` with sample data

**Compliance Schema Additions**:

```prisma
// GDPR Required Models
model ConsentLog {
  id          String   @id @default(cuid())
  sessionId   String?  // For anonymous users
  userId      String?  // For logged-in users
  type        String   // COOKIE, PRIVACY, MARKETING, ANALYTICS
  action      String   // ACCEPT, REJECT, MODIFY
  preferences Json?    // Detailed consent data
  ipAddress   String?
  userAgent   String?
  timestamp   DateTime @default(now())
  validity    DateTime // When consent expires

  @@index([userId])
  @@index([sessionId])
  @@index([timestamp])
  @@index([validity])
}

model DataRequest {
  id          String   @id @default(cuid())
  requestType String   // ACCESS, ERASURE, PORTABILITY, OBJECTION, RESTRICT
  status      String   // PENDING, PROCESSING, COMPLETED, REJECTED
  userId      String?  // null if requested via email
  email       String
  requestDate DateTime @default(now())
  completedAt DateTime?
  responseData Json?    // For portability requests
  rejectionReason String?
  notes       String?
  processedBy String?  // Admin user who processed

  @@index([status])
  @@index([userId])
  @@index([email])
  @@index([requestDate])
}
```

### Phase 3: Legal & Compliance Implementation

**Create** (automated):

1. Cookie banner component with granular controls
2. Privacy policy page
3. Cookie policy page
4. Terms of service page
5. Data deletion API endpoint
6. Data export API endpoint
7. Consent logging middleware
8. Cookie preference management

**Add to Routes**:

```tsx
// app/routes.ts
...prefix(":lang", [
  route("privacy", "routes/$lang/privacy.tsx"),
  route("cookie-policy", "routes/$lang/cookie-policy.tsx"),
  route("terms", "routes/$lang/terms.tsx"),
  route("data-request", "routes/$lang/data-request.tsx"),
  ...
])
```

### Phase 4: Authentication

**Using secure-auth-sdk**:

1. Configure auth with GDPR settings
2. Implement email verification
3. Add password reset flow
4. Create user registration with consent checkboxes
5. Implement data deletion access
6. Add consent management in account settings

**Registration with Consent**:

```tsx
// app/components/auth/RegisterForm.tsx
const RegisterSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8),
  name: z.string().min(2),
  // GDPR: Explicit consent checkboxes
  privacyConsent: z.boolean().refine((val) => val === true, {
    message: "You must accept the privacy policy",
  }),
  marketingConsent: z.boolean().optional(),
  ageConfirmation: z.boolean().refine((val) => val === true, {
    message: "You must confirm you are 16 or older",
  }),
});
```

### Phase 5: Core Pages

**For Each Page**:

1. Create route file with meta tags
2. Create page component
3. Add translations (all languages)
4. Add structured data (SEO)
5. Test responsive design
6. Verify accessibility
7. Test with screen reader

### Phase 6: Testing Implementation

**Create Test Suites**:

1. Unit tests for business logic
2. Integration tests for API
3. E2E tests for critical flows
4. Accessibility tests
5. Performance tests

### Phase 7: Monitoring & Analytics

**Setup**:

1. Configure Sentry for error tracking
2. Setup analytics (with consent)
3. Add performance monitoring
4. Create uptime monitoring
5. Setup alerting

### Phase 8: CI/CD Pipeline

**Create** `.github/workflows/`:

1. Test pipeline
2. Deploy pipeline
3. Security scanning
4. Dependency updates

### Phase 9: Deployment

**Steps**:

1. Configure environment variables
2. Setup staging environment
3. Run smoke tests
4. Deploy to production
5. Verify GDPR compliance
6. Monitor for issues

---

## Testing Strategy

### Unit Testing (Vitest)

**Setup**:

```bash
pnpm add -D vitest @testing-library/react @testing-library/jest-dom @testing-library/user-event jsdom
```

**vitest.config.ts**:

```typescript
import { defineConfig } from "vitest/config";
import react from "@vitejs/plugin-react";
import path from "path";

export default defineConfig({
  plugins: [react()],
  test: {
    environment: "jsdom",
    setupFiles: "./tests/setup.ts",
    coverage: {
      provider: "v8",
      reporter: ["text", "json", "html"],
      exclude: ["node_modules/", "tests/", "**/*.d.ts", "**/*.config.*", "**/mockData/*"],
    },
  },
  resolve: {
    alias: {
      "~": path.resolve(__dirname, "./app"),
    },
  },
});
```

**Test Example**:

```typescript
// tests/unit/components/CookieBanner.test.tsx
import { describe, it, expect, vi, beforeEach, afterEach } from "vitest"
import { render, screen, fireEvent, waitFor } from "@testing-library/react"
import { CookieBanner } from "~/components/legal/CookieBanner"

const mockLocalStorage = {
  getItem: vi.fn(),
  setItem: vi.fn(),
  removeItem: vi.fn(),
  clear: vi.fn(),
}

describe("CookieBanner", () => {
  beforeEach(() => {
    vi.stubGlobal("localStorage", mockLocalStorage)
    mockLocalStorage.getItem.mockReturnValue(null)
  })

  afterEach(() => {
    vi.clearAllMocks()
  })

  it("should show banner when no consent exists", () => {
    render(<CookieBanner />)
    expect(screen.getByText(/we value your privacy/i)).toBeInTheDocument()
  })

  it("should not show banner when consent exists", () => {
    mockLocalStorage.getItem.mockReturnValue(JSON.stringify({
      necessary: true,
      analytics: true,
      marketing: false,
      preferences: true,
    }))

    render(<CookieBanner />)
    expect(screen.queryByText(/we value your privacy/i)).not.toBeInTheDocument()
  })

  it("should save consent when accepting all", async () => {
    render(<CookieBanner />)

    const acceptAllButton = screen.getByText(/accept all/i)
    fireEvent.click(acceptAllButton)

    await waitFor(() => {
      expect(mockLocalStorage.setItem).toHaveBeenCalledWith(
        "cookie_consent",
        expect.stringContaining('"analytics":true')
      )
    })
  })

  it("should save only necessary consent", async () => {
    render(<CookieBanner />)

    const acceptNecessaryButton = screen.getByText(/accept necessary/i)
    fireEvent.click(acceptNecessaryButton)

    await waitFor(() => {
      expect(mockLocalStorage.setItem).toHaveBeenCalledWith(
        "cookie_consent",
        expect.stringContaining('"analytics":false')
      )
    })
  })
})
```

### Integration Testing

**Example**:

```typescript
// tests/integration/api/cookie-consent.test.ts
import { describe, it, expect } from "vitest";
import { loader as cookieConsentLoader } from "~/routes/api/cookie-consent";

describe("Cookie Consent API", () => {
  it("should return consent status", async () => {
    const request = new Request("http://localhost:3000/api/cookie-consent", {
      headers: {
        Cookie: "cookie_consent=%7B%22analytics%22%3Atrue%7D",
      },
    });

    const response = await cookieConsentLoader({ request, params: {}, context: {} });
    const data = await response.json();

    expect(data.analytics).toBe(true);
  });

  it("should update consent preferences", async () => {
    const request = new Request("http://localhost:3000/api/cookie-consent", {
      method: "POST",
      body: JSON.stringify({ analytics: false, marketing: false }),
      headers: {
        "Content-Type": "application/json",
      },
    });

    const response = await cookieConsentLoader({ request, params: {}, context: {} });
    expect(response.status).toBe(200);
  });
});
```

### E2E Testing (Playwright)

**Setup**:

```bash
pnpm add -D @playwright/test
pnpm exec playwright install
```

**playwright.config.ts**:

```typescript
import { defineConfig, devices } from "@playwright/test";

export default defineConfig({
  testDir: "./tests/e2e",
  fullyParallel: true,
  forbidOnly: !!process.env.CI,
  retries: process.env.CI ? 2 : 0,
  workers: process.env.CI ? 1 : undefined,
  reporter: "html",
  use: {
    baseURL: "http://localhost:5173",
    trace: "on-first-retry",
    screenshot: "only-on-failure",
  },
  projects: [
    { name: "chromium", use: { ...devices["Desktop Chrome"] } },
    { name: "firefox", use: { ...devices["Desktop Firefox"] } },
    { name: "webkit", use: { ...devices["Desktop Safari"] } },
    { name: "Mobile Chrome", use: { ...devices["Pixel 5"] } },
    { name: "Mobile Safari", use: { ...devices["iPhone 12"] } },
  ],
  webServer: {
    command: "pnpm dev",
    url: "http://localhost:5173",
    reuseExistingServer: !process.env.CI,
  },
});
```

**Test Examples**:

```typescript
// tests/e2e/gdpr/cookie-consent.spec.ts
import { test, expect } from "@playwright/test";

test.describe("Cookie Consent", () => {
  test("should show cookie banner on first visit", async ({ page }) => {
    await page.goto("/");

    // Clear any existing consent
    await page.context().clearCookies();

    // Reload to see banner
    await page.reload();

    await expect(page.getByText("We value your privacy")).toBeVisible();
    await expect(page.getByText("Accept all")).toBeVisible();
    await expect(page.getByText("Accept necessary only")).toBeVisible();
  });

  test("should accept all cookies", async ({ page }) => {
    await page.goto("/");

    await page.getByText("Accept all").click();

    // Banner should disappear
    await expect(page.getByText("We value your privacy")).not.toBeVisible();

    // Check consent is saved
    const cookies = await page.context().cookies();
    const consentCookie = cookies.find((c) => c.name === "cookie_consent");
    expect(consentCookie).toBeDefined();
  });

  test("should allow customizing preferences", async ({ page }) => {
    await page.goto("/");

    await page.getByText("Customize").click();

    // Wait for preferences panel
    await expect(page.getByText("Cookie Preferences")).toBeVisible();

    // Enable analytics, disable marketing
    await page.getByLabel("analytics").check();
    await page.getByLabel("marketing").uncheck();

    await page.getByText("Save preferences").click();

    // Banner should disappear
    await expect(page.getByText("We value your privacy")).not.toBeVisible();

    // Verify only analytics scripts are loaded
    await page.goto("/");

    // Check for Google Analytics (should be present)
    const gaScript = await page.$('script[src*="google-analytics"]');
    expect(gaScript).toBeTruthy();

    // Check for Facebook Pixel (should NOT be present)
    const fbPixel = await page.$('script[src*="facebook"]');
    expect(fbPixel).toBeNull();
  });

  test("should respect saved preferences on return visit", async ({ page, context }) => {
    // Set consent cookie
    await context.addCookies([
      {
        name: "cookie_consent",
        value: JSON.stringify({
          necessary: true,
          analytics: false,
          marketing: false,
          preferences: true,
        }),
        domain: "localhost",
        path: "/",
      },
    ]);

    await page.goto("/");

    // Banner should NOT appear
    await expect(page.getByText("We value your privacy")).not.toBeVisible();

    // Marketing scripts should NOT be loaded
    const fbPixel = await page.$('script[src*="facebook"]');
    expect(fbPixel).toBeNull();
  });
});
```

**E2E Test for Data Export**:

```typescript
// tests/e2e/gdpr/data-export.spec.ts
import { test, expect } from "@playwright/test";

test.describe("GDPR Data Export", () => {
  test("should allow user to request data export", async ({ page }) => {
    // Login
    await page.goto("/auth/login");
    await page.fill('input[name="email"]', "test@example.com");
    await page.fill('input[name="password"]', "password123");
    await page.click('button[type="submit"]');

    // Navigate to account settings
    await page.goto("/account/settings");

    // Click data export button
    await page.getByText("Download my data").click();

    // Wait for download
    const [download] = await Promise.all([page.waitForEvent("download"), page.getByText("Confirm export").click()]);

    // Verify download
    expect(download.suggestedFilename()).toMatch(/data-export.*\.json/);

    // Verify content
    const data = await download.createReadStream();
    const content = await streamToString(data);
    const jsonData = JSON.parse(content);

    expect(jsonData).toHaveProperty("personalData");
    expect(jsonData).toHaveProperty("orders");
    expect(jsonData).toHaveProperty("addresses");
  });
});

async function streamToString(stream: ReadableStream<Uint8Array>): Promise<string> {
  const reader = stream.getReader();
  let result = "";

  while (true) {
    const { done, value } = await reader.read();
    if (done) break;
    result += new TextDecoder().decode(value);
  }

  return result;
}
```

**Test Coverage Command**:

```bash
# Run all tests with coverage
pnpm test:coverage

# Run E2E tests
pnpm test:e2e

# Run specific test file
pnpm test -- CookieBanner.test.tsx

# Run tests in watch mode
pnpm test --watch
```

---

## Performance Optimization

### Core Web Vitals Targets

```typescript
// Target metrics
const PERFORMANCE_TARGETS = {
  // Largest Contentful Paint: Time to render main content
  LCP: { target: 2500, good: 2500, needsImprovement: 4000 },

  // First Input Delay: Time to respond to first interaction
  FID: { target: 100, good: 100, needsImprovement: 300 },

  // Cumulative Layout Shift: Visual stability
  CLS: { target: 0.1, good: 0.1, needsImprovement: 0.25 },

  // First Contentful Paint: First rendering
  FCP: { target: 1800, good: 1800, needsImprovement: 3000 },

  // Time to Interactive: Page fully interactive
  TTI: { target: 3800, good: 3800, needsImprovement: 7300 },
};
```

### Code Splitting Strategy

```tsx
// app/routes.ts - Lazy load heavy routes
import { lazy, route } from "@react-router/dev/routes";

export default [
  // ... other routes

  // Lazy load admin dashboard
  ...prefix("admin", [
    route(
      "dashboard",
      lazy(() => import("./routes/$lang/admin/dashboard.tsx")),
      {
        // Show loading component while loading
        pendingComponent: () => <LoadingSpinner />,
        // Show error component on error
        errorComponent: ({ error }) => <ErrorPage error={error} />,
      },
    ),
  ]),
];
```

### Image Optimization

**Custom Image Component**:

```tsx
// app/components/ui/OptimizedImage.tsx
import { useState, useRef, useEffect } from "react";
import { cn } from "~/lib/utils";

interface OptimizedImageProps {
  src: string;
  alt: string;
  width?: number;
  height?: number;
  className?: string;
  loading?: "lazy" | "eager";
  priority?: boolean;
}

export function OptimizedImage({ src, alt, width, height, className, loading = "lazy", priority = false }: OptimizedImageProps) {
  const [isLoaded, setIsLoaded] = useState(false);
  const imgRef = useRef<HTMLImageElement>(null);

  useEffect(() => {
    if (!imgRef.current) return;

    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting && imgRef.current) {
            imgRef.current.src = imgRef.current.dataset.src || "";
            observer.unobserve(imgRef.current);
          }
        });
      },
      { rootMargin: "50px" },
    );

    observer.observe(imgRef.current);

    return () => observer.disconnect();
  }, []);

  return (
    <div className={cn("relative overflow-hidden bg-muted", className)} style={{ aspectRatio: width && height ? `${width}/${height}` : undefined }}>
      {!isLoaded && <div className="absolute inset-0 animate-pulse bg-muted" />}

      <img
        ref={imgRef}
        data-src={src}
        alt={alt}
        width={width}
        height={height}
        loading={priority ? "eager" : loading}
        decoding="async"
        className={cn("h-full w-full object-cover transition-opacity duration-300", isLoaded ? "opacity-100" : "opacity-0")}
        onLoad={() => setIsLoaded(true)}
      />
    </div>
  );
}
```

### Lazy Loading Components

```tsx
// Lazy load below-fold components
import { lazy, Suspense } from "react";

const CommentsSection = lazy(() => import("~/components/CommentsSection"));
const NewsletterForm = lazy(() => import("~/components/NewsletterForm"));

export function BlogPost() {
  return (
    <article>
      {/* Critical content - render immediately */}
      <PostContent />

      {/* Below-fold content - lazy load */}
      <Suspense fallback={<CommentsSkeleton />}>
        <CommentsSection postId="123" />
      </Suspense>

      <Suspense fallback={<NewsletterSkeleton />}>
        <NewsletterForm />
      </Suspense>
    </article>
  );
}
```

### Font Optimization

```tsx
// app/root.tsx - Use font-display
export const links: LinksFunction = () => {
  return [
    {
      rel: "stylesheet",
      href: "https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap",
    },
    {
      rel: "preload",
      as: "font",
      type: "font/woff2",
      href: "/fonts/custom.woff2",
      crossOrigin: "anonymous",
    },
  ]
}

// CSS with font-display
@font-face {
  font-family: 'Inter';
  font-style: normal;
  font-weight: 400;
  font-display: swap; /* Critical for FCP */
  src: url('/fonts/inter.woff2') format('woff2');
}
```

### Bundle Analysis

**Add script**:

```bash
# package.json
"scripts": {
  "analyze": "vite-bundle-visualizer"
}
```

**Create** `vite.config.ts`:

```typescript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import { visualizer } from "rollup-plugin-visualizer";

export default defineConfig({
  plugins: [
    react(),
    visualizer({
      filename: "./dist/stats.html",
      open: true,
      gzipSize: true,
      brotliSize: true,
    }),
  ],
});
```

---

## Security Best Practices

### Content Security Policy (CSP)

**Middleware**: `app/middleware/security.ts`

```typescript
import type { Headers } from "react-router";

export function setSecurityHeaders(headers: Headers) {
  // Content Security Policy
  headers.set(
    "Content-Security-Policy",
    [
      "default-src 'self'",
      "script-src 'self' 'unsafe-inline' 'unsafe-eval' https://www.google-analytics.com https://js.stripe.com",
      "style-src 'self' 'unsafe-inline' https://fonts.googleapis.com",
      "img-src 'self' data: https: blob:",
      "font-src 'self' https://fonts.gstatic.com",
      "connect-src 'self' https://api.stripe.com https://www.google-analytics.com",
      "frame-src 'self' https://js.stripe.com https://hooks.stripe.com",
      "object-src 'none'",
      "base-uri 'self'",
      "form-action 'self'",
      "frame-ancestors 'none'",
      "upgrade-insecure-requests",
    ].join("; "),
  );

  // Other security headers
  headers.set("X-Frame-Options", "DENY");
  headers.set("X-Content-Type-Options", "nosniff");
  headers.set("X-XSS-Protection", "1; mode=block");
  headers.set("Referrer-Policy", "strict-origin-when-cross-origin");
  headers.set("Permissions-Policy", "geolocation=(), microphone=(), camera=()");

  // HSTS (only in production with HTTPS)
  if (process.env.NODE_ENV === "production") {
    headers.set("Strict-Transport-Security", "max-age=31536000; includeSubDomains; preload");
  }
}
```

### Rate Limiting

**Middleware**: `app/middleware/rate-limit.ts`

```typescript
import { prisma } from "~/lib/prisma"

const rateLimiter = new Map<string, { count: number; resetTime: number }>()

export async function rateLimit({
  identifier,
  limit = 20,
  window = 60000, // 1 minute
}: {
  identifier: string
  limit?: number
  window?: number
}) {
  const now = Date.now()
  const record = rateLimiter.get(identifier)

  if (!record || now > record.resetTime) {
    rateLimiter.set(identifier, { count: 1, resetTime: now + window })
    return { success: true }
  }

  if (record.count >= limit) {
    // Log to database for monitoring
    await prisma.rateLimitLog.create({
      data: {
        identifier,
        limit,
        window,
        exceededAt: new Date(),
      },
    })

    return { success: false }
  }

  record.count++
  return { success: true }
}

// Prisma model
model RateLimitLog {
  id        String   @id @default(cuid())
  identifier String
  limit     Int
  window    Int
  exceededAt DateTime @default(now())

  @@index([identifier])
  @@index([exceededAt])
}
```

### Input Sanitization

**Utility**: `app/lib/utils/sanitization.ts`

```typescript
import DOMPurify from "isomorphic-dompurify";

export function sanitizeHtml(html: string): string {
  return DOMPurify.sanitize(html, {
    ALLOWED_TAGS: ["p", "br", "strong", "em", "u", "a", "ul", "ol", "li"],
    ALLOWED_ATTR: ["href", "title", "target"],
  });
}

export function sanitizeInput(input: string): string {
  return input
    .trim()
    .replace(/[<>]/g, "") // Remove potential HTML
    .slice(0, 1000); // Limit length
}

export function validateUrl(url: string): boolean {
  try {
    const parsed = new URL(url);
    return ["http:", "https:"].includes(parsed.protocol);
  } catch {
    return false;
  }
}
```

---

## Advanced SEO

### Structured Data (JSON-LD)

**Component**: `app/components/seo/StructuredData.tsx`

```tsx
import { useLoaderData } from "react-router";
import type { Product, Organization, WebSite } from "schema-dts";

interface StructuredDataProps {
  data: Product | Organization | WebSite | (Product | Organization | WebSite)[];
}

export function StructuredData({ data }: StructuredDataProps) {
  const jsonLd = Array.isArray(data) ? data : [data];

  return (
    <script
      type="application/ld+json"
      dangerouslySetInnerHTML={{
        __html: JSON.stringify(jsonLd),
      }}
    />
  );
}

// Usage in product page
export function ProductStructuredData({ product }: { product: Product }) {
  const structuredData: Product = {
    "@type": "Product",
    name: product.name,
    description: product.description,
    image: product.images.map((img) => img.url),
    offers: {
      "@type": "Offer",
      price: product.price,
      priceCurrency: "EUR",
      availability: product.inStock ? "https://schema.org/InStock" : "https://schema.org/OutOfStock",
    },
    brand: {
      "@type": "Brand",
      name: "Your Brand",
    },
  };

  return <StructuredData data={structuredData} />;
}
```

### Dynamic Sitemap

**Route**: `app/routes/sitemap[.]xml.ts`

```typescript
import type { LoaderFunctionArgs } from "react-router";
import { prisma } from "~/lib/prisma";

export const loader = async ({ request }: LoaderFunctionArgs) => {
  const url = new URL(request.url);
  const baseUrl = url.origin;

  // Fetch all pages
  const [products, categories, posts, pages] = await Promise.all([
    prisma.product.findMany({ where: { isActive: true } }),
    prisma.category.findMany({ where: { isActive: true } }),
    prisma.post.findMany({ where: { published: true } }),
    prisma.page.findMany({ where: { published: true } }),
  ]);

  const sitemap = generateSitemap(baseUrl, {
    products,
    categories,
    posts,
    pages,
  });

  return new Response(sitemap, {
    headers: {
      "Content-Type": "application/xml",
      "Cache-Control": "public, max-age=3600",
    },
  });
};

function generateSitemap(
  baseUrl: string,
  data: {
    products: any[];
    categories: any[];
    posts: any[];
    pages: any[];
  },
): string {
  const urls = [
    // Static pages
    { url: baseUrl, changefreq: "daily", priority: 1.0 },
    { url: `${baseUrl}/about`, changefreq: "monthly", priority: 0.8 },
    { url: `${baseUrl}/contact`, changefreq: "monthly", priority: 0.6 },

    // Products
    ...data.products.map((product) => ({
      url: `${baseUrl}/products/${product.slug}`,
      changefreq: "weekly" as const,
      priority: 0.8,
      lastmod: product.updatedAt,
    })),

    // Categories
    ...data.categories.map((category) => ({
      url: `${baseUrl}/category/${category.slug}`,
      changefreq: "weekly" as const,
      priority: 0.7,
    })),

    // Blog posts
    ...data.posts.map((post) => ({
      url: `${baseUrl}/blog/${post.slug}`,
      changefreq: "monthly" as const,
      priority: 0.6,
      lastmod: post.publishedAt,
    })),
  ];

  return `<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
        xmlns:xhtml="http://www.w3.org/1999/xhtml">
  ${urls
    .map(
      (url) => `  <url>
    <loc>${url.url}</loc>
    ${url.lastmod ? `<lastmod>${url.lastmod}</lastmod>` : ""}
    <changefreq>${url.changefreq}</changefreq>
    <priority>${url.priority}</priority>
    ${getAlternateLanguageTags(url.url)}
  </url>`,
    )
    .join("\n")}
</urlset>`;
}

function getAlternateLanguageTags(url: string): string {
  const path = new URL(url).pathname;
  return `
    <xhtml:link rel="alternate" hreflang="en" href="${url}${path}" />
    <xhtml:link rel="alternate" hreflang="it" href="${url}/it${path}" />
    <xhtml:link rel="alternate" hreflang="x-default" href="${url}${path}" />
  `;
}
```

### Robots.txt Generator

**Route**: `app/routes/robots[.]txt.ts`

```typescript
import type { LoaderFunctionArgs } from "react-router";

export const loader = async ({ request }: LoaderFunctionArgs) => {
  const url = new URL(request.url);
  const baseUrl = url.origin;

  const robotsTxt = `# Allow all crawlers
User-agent: *
Allow: /

# Disallow admin areas
Disallow: /admin/
Disallow: /api/
Disallow: /account/

# Disallow search/filter pages
Disallow: /*?filter=*
Disallow: /*?sort=*
Disallow: /*?page=*

# Sitemap location
Sitemap: ${baseUrl}/sitemap.xml

# Crawl delay (optional)
Crawl-delay: 1

# Specific bot rules
User-agent: GPTBot
Disallow: /

User-agent: ChatGPT-User
Disallow: /

User-agent: Google-Extended
Disallow: /
`;

  return new Response(robotsTxt, {
    headers: {
      "Content-Type": "text/plain",
      "Cache-Control": "public, max-age=86400",
    },
  });
};
```

---

## Monitoring & Analytics

### Sentry Integration

**Setup**: `app/lib/monitoring/sentry.ts`

```typescript
import * as Sentry from "@sentry/react-router"
import { useEffect } from "react"
import { useLocation, useNavigation } from "react-router"
import { prisma } from "~/lib/prisma"

if (process.env.NODE_ENV === "production") {
  Sentry.init({
    dsn: process.env.SENTRY_DSN,
    environment: process.env.NODE_ENV,
    tracesSampleRate: 0.1, // 10% of transactions
    replaysSessionSampleRate: 0.1, // 10% of sessions
    replaysOnErrorSampleRate: 1.0, // 100% of errors

    integrations: [
      Sentry.browserTracingIntegration({
        useEffect,
        useLocation,
        useNavigation,
      }),
      Sentry.replayIntegration(),
    ],

    beforeSend(event, hint) {
      // Filter sensitive data
      if (event.request) {
        delete event.request.cookies
      }

      // Log error to database
      logErrorToDatabase(event, hint)

      return event
    },
  })
}

async function logErrorToDatabase(event: any, hint: any) {
  try {
    await prisma.errorLog.create({
      data: {
        eventId: event.event_id,
        message: event.message || hint.originalException?.message,
        level: event.level,
        transaction: event.transaction,
        timestamp: new Date(event.timestamp * 1000),
        tags: event.tags as any,
        extra: event.extra as any,
        request: event.request as any,
        userId: event.user?.id,
      },
    })
  } catch (error) {
    console.error("Failed to log error to database:", error)
  }
}

// Prisma model
model ErrorLog {
  id          String   @id @default(cuid())
  eventId     String   @unique
  message     String
  level       String
  transaction String?
  timestamp   DateTime
  tags        Json?
  extra       Json?
  request     Json?
  userId      String?

  @@index([timestamp])
  @@index([level])
  @@index([userId])
}
```

### Privacy-First Analytics (Plausible)

**Component**: `app/components/analytics/Plausible.tsx`

```tsx
import { useEffect } from "react";
import { useLocation } from "react-router";

export function PlausibleAnalytics() {
  const location = useLocation();

  useEffect(() => {
    // Check for cookie consent
    const consent = localStorage.getItem("cookie_consent");
    if (!consent) return;

    const { analytics } = JSON.parse(consent);
    if (!analytics) return;

    // Load Plausible script
    const script = document.createElement("script");
    script.src = "https://plausible.io/js/script.js";
    script.dataset.domain = window.location.hostname;
    script.async = true;
    script.defer = true;

    document.head.appendChild(script);

    return () => {
      document.head.removeChild(script);
    };
  }, []);

  // Track page views
  useEffect(() => {
    const consent = localStorage.getItem("cookie_consent");
    if (!consent) return;

    const { analytics } = JSON.parse(consent);
    if (!analytics) return;

    if (window.plausible) {
      window.plausible("pageview", {
        url: location.pathname,
      });
    }
  }, [location]);

  return null;
}

// Type declaration
declare global {
  interface Window {
    plausible?: (event: string, props?: Record<string, unknown>) => void;
  }
}
```

### Performance Monitoring

**Component**: `app/components/monitoring/WebVitals.tsx`

```typescript
import { useEffect } from "react";

export function WebVitals() {
  useEffect(() => {
    let isSupported = "PerformanceObserver" in window;

    if (!isSupported) return;

    // Track LCP
    const lcpObserver = new PerformanceObserver((list) => {
      const entries = list.getEntries();
      const lastEntry = entries[entries.length - 1] as any;
      const lcp = Math.round(lastEntry.renderTime || lastEntry.loadTime);

      sendToAnalytics("LCP", lcp);
    });
    lcpObserver.observe({ entryTypes: ["largest-contentful-paint"] });

    // Track FID
    const fidObserver = new PerformanceObserver((list) => {
      const entries = list.getEntries();
      entries.forEach((entry: any) => {
        const fid = Math.round(entry.processingStart - entry.startTime);
        sendToAnalytics("FID", fid);
      });
    });
    fidObserver.observe({ entryTypes: ["first-input"] });

    // Track CLS
    let clsValue = 0;
    const clsObserver = new PerformanceObserver((list) => {
      list.getEntries().forEach((entry: any) => {
        if (!entry.hadRecentInput) {
          clsValue += entry.value;
          sendToAnalytics("CLS", clsValue);
        }
      });
    });
    clsObserver.observe({ entryTypes: ["layout-shift"] });

    return () => {
      lcpObserver.disconnect();
      fidObserver.disconnect();
      clsObserver.disconnect();
    };
  }, []);

  return null;
}

function sendToAnalytics(name: string, value: number) {
  // Only send if consent given
  const consent = localStorage.getItem("cookie_consent");
  if (!consent) return;

  const { analytics } = JSON.parse(consent);
  if (!analytics) return;

  if (window.gtag) {
    window.gtag("event", name, {
      value,
      event_category: "Web Vitals",
    });
  }
}
```

---

## Accessibility (WCAG 2.1 AA)

### Skip Links

**Component**: `app/components/a11y/SkipLinks.tsx`

```tsx
export function SkipLinks() {
  return (
    <div className="sr-only focus-within:not-sr-only">
      <a
        href="#main-content"
        className="focus:absolute focus:left-4 focus:top-4 focus:z-50 focus:rounded-md focus:bg-primary focus:px-4 focus:py-2 focus:text-primary-foreground"
      >
        Skip to main content
      </a>
      <a
        href="#main-navigation"
        className="focus:absolute focus:left-4 focus:top-12 focus:z-50 focus:rounded-md focus:bg-primary focus:px-4 focus:py-2 focus:text-primary-foreground"
      >
        Skip to navigation
      </a>
    </div>
  );
}
```

### ARIA Live Regions

**Example**: `app/components/a11y/LiveAnnouncer.tsx`

```tsx
import { useEffect, useState } from "react";

export function LiveAnnouncer() {
  const [announcement, setAnnouncement] = useState("");

  useEffect(() => {
    const handleAnnouncement = (e: CustomEvent) => {
      setAnnouncement(e.detail.message);
      setTimeout(() => setAnnouncement(""), 1000);
    };

    window.addEventListener("announce", handleAnnouncement as EventListener);
    return () => window.removeEventListener("announce", handleAnnouncement as EventListener);
  }, []);

  return (
    <div role="status" aria-live="polite" aria-atomic="true" className="sr-only">
      {announcement}
    </div>
  );
}

// Usage
function announceToScreenReader(message: string) {
  window.dispatchEvent(new CustomEvent("announce", { detail: { message } }));
}
```

### Focus Management

**Hook**: `app/lib/hooks/useFocusManagement.ts`

```typescript
import { useEffect, useRef } from "react";

export function useFocusTrap(enabled: boolean) {
  const containerRef = useRef<HTMLDivElement>(null);

  useEffect(() => {
    if (!enabled) return;

    const container = containerRef.current;
    if (!container) return;

    const focusableElements = container.querySelectorAll(
      'a[href], button:not([disabled]), textarea:not([disabled]), input:not([disabled]), select:not([disabled]), [tabindex]:not([tabindex="-1"])',
    );

    const firstElement = focusableElements[0] as HTMLElement;
    const lastElement = focusableElements[focusableElements.length - 1] as HTMLElement;

    const handleTab = (e: KeyboardEvent) => {
      if (e.key !== "Tab") return;

      if (e.shiftKey) {
        if (document.activeElement === firstElement) {
          lastElement.focus();
          e.preventDefault();
        }
      } else {
        if (document.activeElement === lastElement) {
          firstElement.focus();
          e.preventDefault();
        }
      }
    };

    container.addEventListener("keydown", handleTab);
    firstElement?.focus();

    return () => {
      container.removeEventListener("keydown", handleTab);
    };
  }, [enabled]);

  return containerRef;
}
```

### Color Contrast Checker

**Utility**: `app/lib/utils/a11y.ts`

```typescript
export function getContrastRatio(foreground: string, background: string): number {
  const lum1 = getLuminance(foreground);
  const lum2 = getLuminance(background);
  const brightest = Math.max(lum1, lum2);
  const darkest = Math.min(lum1, lum2);

  return (brightest + 0.05) / (darkest + 0.05);
}

function getLuminance(hex: string): number {
  const rgb = hexToRgb(hex);
  if (!rgb) return 0;

  const [r, g, b] = rgb.map((val) => {
    val = val / 255;
    return val <= 0.03928 ? val / 12.92 : Math.pow((val + 0.055) / 1.055, 2.4);
  });

  return 0.2126 * r + 0.7152 * g + 0.0722 * b;
}

function hexToRgb(hex: string): [number, number, number] | null {
  const result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
  return result ? [parseInt(result[1], 16), parseInt(result[2], 16), parseInt(result[3], 16)] : null;
}

export function meetsWCAG(foreground: string, background: string, level: "AA" | "AAA" = "AA", largeText: boolean = false): boolean {
  const ratio = getContrastRatio(foreground, background);

  if (largeText) {
    return level === "AA" ? ratio >= 3 : ratio >= 4.5;
  }

  return level === "AA" ? ratio >= 4.5 : ratio >= 7;
}
```

---

## CI/CD Pipeline

### GitHub Actions

**File**: `.github/workflows/ci.yml`

```yaml
name: CI

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main, develop]

jobs:
  # Type checking and linting
  type-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: pnpm/action-setup@v2
        with:
          version: 8

      - uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "pnpm"

      - name: Install dependencies
        run: pnpm install --frozen-lockfile

      - name: Run type check
        run: pnpm tsc --noEmit

      - name: Run linter
        run: pnpm lint

      - name: Check formatting
        run: pnpm biome format --check .

  # Run tests
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: pnpm/action-setup@v2
        with:
          version: 8

      - uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "pnpm"

      - name: Install dependencies
        run: pnpm install --frozen-lockfile

      - name: Setup database
        run: pnpm db:push --skip-generate
        env:
          DATABASE_URL: ${{ secrets.DATABASE_URL }}

      - name: Run unit tests
        run: pnpm test:coverage

      - name: Upload coverage
        uses: codecov/codecov-action@v3
        with:
          files: ./coverage/coverage-final.json

  # E2E tests
  e2e:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: pnpm/action-setup@v2
        with:
          version: 8

      - uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "pnpm"

      - name: Install dependencies
        run: pnpm install --frozen-lockfile

      - name: Install Playwright
        run: pnpm exec playwright install --with-deps

      - name: Build application
        run: pnpm build

      - name: Run E2E tests
        run: pnpm test:e2e

      - uses: actions/upload-artifact@v3
        if: always()
        with:
          name: playwright-report
          path: playwright-report/
          retention-days: 30

  # Security audit
  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: pnpm/action-setup@v2
        with:
          version: 8

      - uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "pnpm"

      - name: Run security audit
        run: pnpm audit --audit-level=moderate

      - name: Check for vulnerabilities
        run: pnpm audit --prod
```

**File**: `.github/workflows/deploy.yml`

```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: pnpm/action-setup@v2
        with:
          version: 8

      - uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "pnpm"

      - name: Install dependencies
        run: pnpm install --frozen-lockfile

      - name: Run tests
        run: pnpm test:run

      - name: Build application
        run: pnpm build
        env:
          DATABASE_URL: ${{ secrets.DATABASE_URL }}
          SENTRY_AUTH_TOKEN: ${{ secrets.SENTRY_AUTH_TOKEN }}

      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v20
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-args: "--prod"

      - name: Run smoke tests
        run: pnpm test:e2e --project=chromium
        env:
          BASE_URL: ${{ secrets.PRODUCTION_URL }}
```

---

## Progressive Web App

### Service Worker

**File**: `public/sw.js`

```javascript
const CACHE_NAME = "v1";
const STATIC_CACHE = [
  "/",
  "/offline",
  "/manifest.json",
  // Add other critical assets
];

// Install event - cache static assets
self.addEventListener("install", (event) => {
  event.waitUntil(caches.open(CACHE_NAME).then((cache) => cache.addAll(STATIC_CACHE)));
  self.skipWaiting();
});

// Activate event - clean old caches
self.addEventListener("activate", (event) => {
  event.waitUntil(
    caches.keys().then((cacheNames) => {
      return Promise.all(cacheNames.filter((name) => name !== CACHE_NAME).map((name) => caches.delete(name)));
    }),
  );
  self.clients.claim();
});

// Fetch event - network first, then cache
self.addEventListener("fetch", (event) => {
  const { request } = event;
  const url = new URL(request.url);

  // Skip non-GET requests
  if (request.method !== "GET") return;

  // Skip external requests
  if (url.origin !== location.origin) return;

  // Skip API routes
  if (url.pathname.startsWith("/api/")) return;

  event.respondWith(
    fetch(request)
      .then((response) => {
        // Cache successful responses
        if (response.status === 200) {
          const clone = response.clone();
          caches.open(CACHE_NAME).then((cache) => cache.put(request, clone));
        }
        return response;
      })
      .catch(() => {
        // Fallback to cache
        return caches.match(request).then((cached) => {
          if (cached) return cached;

          // Offline fallback for HTML pages
          if (request.headers.get("accept")?.includes("text/html")) {
            return caches.match("/offline");
          }
        });
      }),
  );
});
```

### Manifest

**File**: `public/manifest.json`

```json
{
  "name": "Your Site Name",
  "short_name": "SiteName",
  "description": "Description of your site",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#000000",
  "orientation": "portrait-primary",
  "icons": [
    {
      "src": "/icons/icon-72x72.png",
      "sizes": "72x72",
      "type": "image/png",
      "purpose": "maskable any"
    },
    {
      "src": "/icons/icon-96x96.png",
      "sizes": "96x96",
      "type": "image/png",
      "purpose": "maskable any"
    },
    {
      "src": "/icons/icon-128x128.png",
      "sizes": "128x128",
      "type": "image/png",
      "purpose": "maskable any"
    },
    {
      "src": "/icons/icon-144x144.png",
      "sizes": "144x144",
      "type": "image/png",
      "purpose": "maskable any"
    },
    {
      "src": "/icons/icon-152x152.png",
      "sizes": "152x152",
      "type": "image/png",
      "purpose": "maskable any"
    },
    {
      "src": "/icons/icon-192x192.png",
      "sizes": "192x192",
      "type": "image/png",
      "purpose": "maskable any"
    },
    {
      "src": "/icons/icon-384x384.png",
      "sizes": "384x384",
      "type": "image/png",
      "purpose": "maskable any"
    },
    {
      "src": "/icons/icon-512x512.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "maskable any"
    }
  ],
  "categories": ["shopping", "business"],
  "screenshots": [
    {
      "src": "/screenshots/desktop-wide.png",
      "sizes": "1280x720",
      "type": "image/png",
      "form_factor": "wide"
    },
    {
      "src": "/screenshots/mobile-narrow.png",
      "sizes": "750x1334",
      "type": "image/png",
      "form_factor": "narrow"
    }
  ]
}
```

### Service Worker Registration

**File**: `app/entry.client.tsx`

```typescript
import { hydrateRoot } from "react-router/dom";
import { HydrationState } from "react-router";
import { makeRoute } from "react-router";

// Register service worker
if ("serviceWorker" in navigator && import.meta.env.PROD) {
  window.addEventListener("load", () => {
    navigator.serviceWorker
      .register("/sw.js")
      .then((registration) => {
        console.log("SW registered:", registration);

        // Check for updates
        registration.addEventListener("updatefound", () => {
          const newWorker = registration.installing;
          if (newWorker) {
            newWorker.addEventListener("statechange", () => {
              if (newWorker.state === "installed" && navigator.serviceWorker.controller) {
                // New version available
                if (confirm("New version available. Reload to update?")) {
                  window.location.reload();
                }
              }
            });
          }
        });
      })
      .catch((error) => {
        console.error("SW registration failed:", error);
      });
  });
}
```

---

## Code Templates & Patterns

### GDPR-Compliant Form

```tsx
// app/components/forms/GDPRForm.tsx
import { useForm } from "@hookform/resolvers/zod";
import { useForm as useHookForm } from "react-hook-form";
import { z } from "zod";

const GDPRSchemas = z.object({
  // Your form fields
  name: z.string().min(2),
  email: z.string().email(),

  // GDPR consent checkboxes
  privacyPolicy: z.boolean().refine((val) => val === true, {
    message: "You must accept the privacy policy",
  }),
  marketingConsent: z.boolean().optional(),
  dataProcessing: z.boolean().refine((val) => val === true, {
    message: "You must consent to data processing",
  }),
});

export function GDPRForm() {
  const form = useHookForm({
    resolver: useForm(GDPRSchemas),
  });

  const onSubmit = async (data: z.infer<typeof GDPRSchemas>) => {
    // Log consent
    await logConsent({
      type: "FORM_SUBMISSION",
      privacyPolicy: data.privacyPolicy,
      marketingConsent: data.marketingConsent ?? false,
      dataProcessing: data.dataProcessing,
    });

    // Submit form
    // ...
  };

  return (
    <form onSubmit={form.handleSubmit(onSubmit)}>
      {/* Your form fields */}

      <div className="space-y-4">
        {/* Required consents */}
        <label className="flex items-start gap-3">
          <input type="checkbox" {...form.register("privacyPolicy")} className="mt-1" />
          <span className="text-sm">
            I have read and agree to the{" "}
            <Link to="/privacy" className="underline">
              Privacy Policy
            </Link>{" "}
            and{" "}
            <Link to="/terms" className="underline">
              Terms of Service
            </Link>
            * (required)
          </span>
        </label>

        <label className="flex items-start gap-3">
          <input type="checkbox" {...form.register("dataProcessing")} className="mt-1" />
          <span className="text-sm">I consent to the processing of my personal data * (required)</span>
        </label>

        {/* Optional consent */}
        <label className="flex items-start gap-3">
          <input type="checkbox" {...form.register("marketingConsent")} className="mt-1" />
          <span className="text-sm">I would like to receive marketing communications and newsletters (optional)</span>
        </label>
      </div>

      {form.formState.errors.privacyPolicy && <p className="text-sm text-destructive">{form.formState.errors.privacyPolicy.message}</p>}
    </form>
  );
}
```

---

## Quality Checklist

### ✅ GDPR & Legal Compliance

- [ ] Cookie consent banner with granular controls
- [ ] Privacy policy page (GDPR Articles 13 & 14)
- [ ] Cookie policy page
- [ ] Terms of service page
- [ ] Data deletion API endpoint
- [ ] Data export API endpoint
- [ ] Consent logging
- [ ] Cookie preference management
- [ ] Right to access form
- [ ] Right to erasure form
- [ ] Double opt-in for newsletters
- [ ] Age verification (if under 16)

### ✅ Testing

- [ ] Unit tests for business logic (80%+ coverage)
- [ ] Integration tests for API endpoints
- [ ] E2E tests for critical user flows
- [ ] Accessibility tests (WCAG 2.1 AA)
- [ ] Performance tests (Core Web Vitals)
- [ ] Security tests (OWASP Top 10)

### ✅ Performance

- [ ] LCP < 2.5s
- [ ] FID < 100ms
- [ ] CLS < 0.1
- [ ] Code splitting implemented
- [ ] Lazy loading for images
- [ ] Font optimization (font-display: swap)
- [ ] Bundle size optimized
- [ ] CDN for static assets

### ✅ Security

- [ ] Content Security Policy (CSP)
- [ ] X-Frame-Options: DENY
- [ ] X-Content-Type-Options: nosniff
- [ ] Rate limiting on sensitive endpoints
- [ ] Input validation (Zod)
- [ ] Output sanitization
- [ ] SQL injection prevention (Prisma)
- [ ] XSS protection
- [ ] CSRF protection on forms
- [ ] HTTPS only in production

### ✅ SEO

- [ ] Meta tags on all pages
- [ ] Structured data (JSON-LD)
- [ ] Dynamic sitemap.xml
- [ ] robots.txt
- [ ] Canonical URLs
- [ ] Open Graph tags
- [ ] Twitter Cards
- [ ] Schema.org markup
- [ ] Image alt tags
- [ ] Semantic HTML

### ✅ Accessibility

- [ ] WCAG 2.1 AA compliant
- [ ] Keyboard navigation works
- [ ] Screen reader friendly
- [ ] Focus management
- [ ] ARIA labels where needed
- [ ] Color contrast ratio 4.5:1 minimum
- [ ] Skip links
- [ ] Form labels properly associated
- [ ] Error messages accessible

### ✅ Monitoring & Analytics

- [ ] Error tracking (Sentry)
- [ ] Performance monitoring
- [ ] Privacy-first analytics (with consent)
- [ ] Uptime monitoring
- [ ] Log aggregation

### ✅ Code Quality

- [ ] TypeScript strict mode
- [ ] No console errors
- [ ] Biome linting passes
- [ ] Code formatted
- [ ] No `any` types without justification
- [ ] Proper error handling
- [ ] Consistent code patterns

### ✅ DevOps

- [ ] CI/CD pipeline configured
- [ ] Automated testing
- [ ] Staging environment
- [ ] Database migrations
- [ ] Environment variables documented
- [ ] Rollback procedure

---

## Environment Variables

```env
# Database
DATABASE_URL="postgresql://user:password@host:5432/dbname"

# Authentication
AUTH_SECRET="[min 32 characters]"
SESSION_SECRET="[min 32 characters]"
PUBLIC_APP_URL="https://yourdomain.com"

# Email (Resend)
RESEND_API_KEY="re_..."
RESEND_FROM_EMAIL="noreply@yourdomain.com"
RESEND_FROM_NAME="Your Site Name"

# Payments (Stripe)
STRIPE_SECRET_KEY="sk_test_..."
STRIPE_WEBHOOK_SECRET="whsec_..."
STRIPE_PUBLISHABLE_KEY="pk_test_..."

# Storage (Supabase)
SUPABASE_URL="https://..."
SUPABASE_ANON_KEY="eyJ..."
SUPABASE_SERVICE_ROLE_KEY="eyJ..."

# Monitoring (Sentry)
SENTRY_DSN="https://..."
SENTRY_AUTH_TOKEN="..."

# Deployment (Vercel)
VERCEL_TOKEN="..."
VERCEL_ORG_ID="..."
VERCEL_PROJECT_ID="..."

# Analytics (Plausible)
PLAUSIBLE_DOMAIN="yourdomain.com"

# OAuth (if enabled)
GOOGLE_CLIENT_ID="..."
GOOGLE_CLIENT_SECRET="..."
GITHUB_CLIENT_ID="..."
GITHUB_CLIENT_SECRET="..."
```

---

## Next Steps After Generation

```bash
# 1. Install dependencies
pnpm install

# 2. Set up environment variables
cp .env.example .env
# Edit .env with your values

# 3. Set up database
pnpm db:push    # or pnpm db:migrate
pnpm db:seed

# 4. Run tests
pnpm test        # Unit tests
pnpm test:e2e    # E2E tests

# 5. Run linter
pnpm lint
pnpm typecheck

# 6. Start development server
pnpm dev

# 7. Verify GDPR compliance
# - Check cookie banner appears
# - Verify consent preferences work
# - Test data deletion API
# - Test data export API
# - Verify all legal pages exist

# 8. Deploy to staging
pnpm build
# Deploy to staging environment

# 9. Run smoke tests on staging
pnpm test:e2e --project=chromium

# 10. Deploy to production
# After all tests pass and manual verification complete
```

---

## Support & Maintenance

### Regular Maintenance Tasks

**Weekly**:

- Review error logs in Sentry
- Check performance metrics
- Review security advisories
- Verify backups

**Monthly**:

- Update dependencies (`pnpm update`)
- Review and update legal pages if needed
- Audit access logs
- Test disaster recovery

**Quarterly**:

- Full security audit
- Performance review
- Accessibility audit
- SEO review

---

**This skill generates enterprise-grade, GDPR-compliant websites following 2025 best practices. All sites include cookie consent, legal pages, data portability, and comprehensive testing.**

_Generated sites are production-ready and can be deployed immediately._
