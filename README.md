# Custom Sidebar

This is an extra module for [Home Assistant Frontend](https://www.home-assistant.io/integrations/frontend/#extra_module_url) on [Home Assistant](https://www.home-assistant.io/)

This plugin allows you to rearrange items in the Home Assistant sidebar. (Overview, Map, History, etc)

## Installation

### Step 1

Install `custom-sidebar` by copying `custom-sidebar.js` from this repo to `<config directory>/www/custom-sidebar.js` on your Home Assistant instance.

### Step 2

To load the module into your instance you will need to add it to the frontend configuration in configuration.yaml.

Ex:
```yaml
frontend:
  extra_module_url:
    - /local/custom-sidebar.js
```

### Step 3

The order configuration must be stored in `<config directory>/www/sidebar-order.yaml`. You will create this file yourself. All items will be under the root `order:`.
They will be arranged in order from top to bottom.

Ex:
```yaml
order:
  - item: map
  - item: developer tools
  - item: overview
  - item: history
    bottom: true
  - item: logbook
    bottom: true
```

## Item Options

| Name | Type | Requirement | Description
| ---- | ---- | ------- | -----------
| item | string | **Required** | This is a string that will be checked for in the display name of the sidebar item. It can be a substring such as `developer` instead of `Developer Tools`. It is not case sensitive.
| bottom | boolean | **Optional** | Setting this option to `true` will group the item with the bottom items (Configuration, Developer Tools, etc) instead of at the top.
| hide | boolean | **Optional** | Hide item in sidebar.

NOTE: If you are using a language other than English make sure to include both the English word and a second entry with the translated word that is displayed in your browser for the `item: ` portion of the config. This will ensure that the item is moved/hidden regardless of the time at which it is rendered.
Example: Language Portuguese
```yaml
  - item: history
    hidden: true
  - item: Histórico
    hidden: true
```
