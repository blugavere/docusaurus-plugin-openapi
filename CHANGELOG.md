## 0.3.0 (Dec 16, 2021)

High level enhancements

- Docusaurus beta.13 support (Thanks @Josh-Cena!)

  ```js
  // Be sure to update @docusaurus/core:
  "dependencies": {
    "@docusaurus/core": "2.0.0-beta.13",
    // ...
  }
  ```

- The OpenAPI `info` stanza will now generate an "Introduction" page

  ```yaml
  openapi: 3.0.3
  info:
    title: Swagger Petstore
    version: 1.0.0
    description: |
      This is a sample server Petstore server.
      You can find out more about Swagger at
      [http://swagger.io](http://swagger.io) or on [irc.freenode.net, #swagger](http://swagger.io/irc/).
      For this sample, you can use the api key `special-key` to test the authorization filters.
  ```

- Request bodies will now render JSON Schema with the use of `allOf` keywords

  ```yaml
  requestBody:
    content:
      description: Example request
      application/json:
        schema:
          allOf:
            - $ref: "#/components/schema/Example1"
            - $ref: "#/components/schema/Example2"
  ```

- Enum options will now be displayed in schema tables
  <table>
  <tbody>
  <tr>
  <td>

  `status` string

  Enum: `"available"`, `"pending"`, `"sold"`

  Pet status in the store

  </td>
  </tr>
  </tbody>
  </table>

Other enhancements and bug fixes

- Initial proxy code ([#97](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/97))
- Add support for an introduction page ([#94](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/94))
- Add `allOf` JSON schema support ([#96](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/96))
- Display enum values in tables ([#93](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/93))
- Initial plugin refactor ([#86](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/86))
- Upgrade to Docusaurus beta.13 ([#88](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/88))

## 0.2.3 (Dec 11, 2021)

Enhancements and bug fixes

- Add case-insensitive security scheme support ([#83](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/83))
- Add CodeSandbox CI ([#77](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/77))

## 0.2.2 (Dec 6, 2021)

Fix broken package

## 0.2.1 (Dec 5, 2021)

High level enhancements

- The demo panel now allows you to choose the security scheme from a dropdown that is populated by the OpenAPI definition (only showing the dropdown if more than one is listed)
- Adds support for using multiple auth modes simultaneously (Eg: `(BearerAuth) OR (ApiKeyAuth AND BasicAuth)`)
- Adds an `authPersistence` option to `themeConfig.api`. Defaults to `"localStorage"`, can be set to `false` to disable or `sessionStorage` to only persist while the window is open.

Other enhancements and bug fixes

- Add better auth support ([#74](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/74))

## 0.2.0 (Dec 4, 2021)

### 💥 Breaking Changes

The plugin option `openapiPath` has been renamed to `path` and no longer needs to be wrapped in `require.resolve`.

As recomended my the [Docusaurus documentation](https://docusaurus.io/docs/presets), the plugin `docusaurus-plugin-api` has been properly split into 3 packages:

- `docusaurus-preset-api`
- `docusaurus-plugin-api`
- `docusaurus-theme-api`

The package `docusaurus-plugin-api` will no longer work on it's own without `docusaurus-theme-api`. Instead, the preset `docusaurus-preset-api` can be used on it's own and act as a drop-in replacement for `@docusaurus/preset-classic`.

Example usage:

```diff
// docusaurus.config.js

const config = {
-  plugins: [
-    [
-      "docusaurus-plugin-openapi",
-      {
-        openapiPath: require.resolve("./examples/openapi.json"),
-      },
-    ],
-  ],

  presets: [
    [
-      "@docusaurus/preset-classic",
+      "docusaurus-preset-openapi",
      {
+        api: {
+          path: "examples/openapi.json",
+        }
        docs: {
          // doc options ...
        },
        blog: {
         // blog options ...
        },
        theme: {
          customCss: require.resolve("./src/css/custom.css"),
        },
      },
    ],
  ],
}
```

Other enhancements and bug fixes

- Fix multi plugin bug ([#69](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/69))
- Add yaml support ([#68](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/68))
- Generate markdown for full page ([#65](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/65))
- Refactor plugin into separate packages ([#64](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/64))
- Update documentation ([#63](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/63))

## 0.1.1 (Nov 24, 2021)

Enhancements and bug fixes

- Fix missing status code description ([#61](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/61))
- Fix narrow tables style regression ([#55](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/55))

## 0.1.0 (Nov 4, 2021)

Enhancements and bug fixes

- Update project structure ([#52](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/52))
- Update plugin to support Docusaurus 2.0.0 beta ([#51](https://github.com/cloud-annotations/docusaurus-plugin-openapi/pull/51))
