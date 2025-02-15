---
layout: ~/layouts/MainLayout.astro
title: Testen
description: Eine Einführung in das Testen in Astro
i18nReady: false
setup: import PackageManagerTabs from '~/components/tabs/PackageManagerTabs.astro'
---
Testen hilft dir, funktionierenden Astro-Code zu schreiben und zu warten. Astro unterstützt viele beliebte Tools für Unit-Tests, Komponenten-Tests und End-to-End-Tests, darunter Jest, Mocha, Jasmine, Cypress und Playwright. Du kannst sogar Framework-spezifische Testbibliotheken wie React Testing Library installieren, um deine UI-Framework-Komponenten zu testen.

Test-Frameworks ermöglichen es dir, **Aussagen** oder **Erwartungen** über das Verhalten deines Codes in bestimmten Situationen zu formulieren und diese mit dem tatsächlichen Verhalten deines aktuellen Codes zu vergleichen.

## Playwright

Playwright ist ein End-to-End Test-Framework für moderne Web-Apps. Verwende die Playwright-API in JavaScript oder TypeScript, um deinen Astro-Code auf allen modernen Rendering-Engines, darunter Chromium, WebKit und Firefox, zu testen.

### Installation

Du kannst mit der [VS Code-Erweiterung](https://playwright.dev/docs/getting-started-vscode) beginnen und deine Tests ausführen.

Alternativ kannst du Playwright in deinem Astro-Projekt mit dem von dir gewählten Paketmanager installieren. Folge den CLI-Schritten, um JavaScript/TypeScript, den Namen deines Test-Ordners und einen optionalen GitHub Actions-Workflow auszuwählen.

<PackageManagerTabs>
  <Fragment slot="npm">
  ```shell
  npm init playwright@latest
  ```
  </Fragment>
  <Fragment slot="pnpm">
  ```shell
  pnpm dlx create-playwright
  ```
  </Fragment>
  <Fragment slot="yarn">
  ```shell
  yarn create playwright
  ```
  </Fragment>
</PackageManagerTabs>

### Erstelle deinen ersten Playwright-Test

1. Wähle eine Seite zum Testen aus. Wir verwenden die unten stehende `index.astro`-Seite als Beispiel.

```html title="src/pages/index.astro"
---
---
<html lang="de">
  <head>
    <title>Astro ist fantastisch!</title>
    <meta name='description' content="Beziehe Inhalte von überall und stelle sie schnell mit Astros Insel-Architektur der nächsten Generation bereit." />
  </head>
  <body></body>
</html>
```

2. Erstelle einen neuen Ordner und füge nachstehende Testdatei in `src/test` hinzu. Kopiere und füge den nachfolgenden Test in deine Datei ein, um zu verifizieren, dass die Metainformationen der Seite korrekt sind. Aktualisiere den `<title>`-Wert entsprechend der Seite, die du testest.

```jsx title="src/test/index.spec.ts" "Astro ist fantastisch!"
test('Metadaten sind korrekt', async ({ page }) => {
  await page.goto("http://localhost:3000/");

  await expect(page).toHaveTitle('Astro ist fantastisch!');
});
```

:::tip[Eine Basis-URL setzen]
Du kannst [`"baseURL": "http://localhost:3000"`](https://playwright.dev/docs/api/class-testoptions#test-options-base-url) in der `playwright.config.ts`-Konfigurationsdatei setzen, um `page.goto("/")` anstatt `page.goto("http://localhost:3000/")` als komfortablere URL zu nutzen.
:::

### Deine Playwright-Tests ausführen 

Du kannst einen einzelnen oder mehrere Tests auf einmal ausführen und dabei einen oder mehrere Browser testen. Standardmäßig werden deine Testergebnisse im Terminal angezeigt. Optional kannst du den HTML-Test-Reporter öffnen, um einen vollständigen Bericht anzuzeigen und die Testergebnisse zu filtern.

1. Um unseren Test aus dem vorherigen Beispiel mit der Kommandozeile auszuführen, nutze das `test`-Kommando. Optional kannst du den Dateinamen angeben, um nur den einzelnen Test auszuführen.

```sh
npx playwright test index.spec.ts
```

2. Um den vollständigen HTML-Testbericht anzusehen, öffne ihn mit folgendem Befehl:
```sh
npx playwright show-report
```

:::tip
Führe deine Tests gegen deinen Produktions-Code aus, um näher an deine live gehostete Seite heranzukommen.
:::

#### Fortgeschritten: Einen Entwicklungs-Webserver während deiner Tests starten 

Du kannst Playwright auch deinen Server starten lassen, wenn du dein Test-Skript mit der [`webServer`](https://playwright.dev/docs/test-advanced#launching-a-development-web-server-during-the-tests)-Option in der Playwright-Konfigurationsdatei ausführst.

Hier ist ein Beispiel der Konfiguration und Kommandos, wenn du Yarn verwendest:

1. Füge ein Test-Skript wie: `"test:e2e": "yarn playwright"` in deine `package.json`-Datei im Projekt&shy;stamm&shy;verzeichnis ein.

2. Füge in der `playwright.config.ts` das `webServer`-Objekt hinzu und aktualisiere den `command`-Wert zu `yarn preview`.
```js title="playwright.config.ts" ins={3-8} "yarn preview"
import type { PlaywrightTestConfig } from '@playwright/test';
const config: PlaywrightTestConfig = {
  webServer: {
    command: 'yarn preview',
    url: 'http://localhost:3000/app/',
    timeout: 120 * 1000,
    reuseExistingServer: !process.env.CI,
  },
  use: {
    baseURL: 'http://localhost:3000/app/',
  },
};
export default config;
```

3. Führe `yarn build` und anschließend `yarn test:e2e` aus, um deine Playwright-Tests auszuführen.

Weiterführende Informationen über Playwright können mit den folgenden Links gefunden werden:

- [Erste Schritte mit Playwright](https://playwright.dev/docs/intro)
- [Einen Entwicklungs-Server verwenden](https://playwright.dev/docs/test-advanced#launching-a-development-web-server-during-the-tests)
