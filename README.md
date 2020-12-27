# Timeline Plugin

**Table of Contents**
- [Description](#description)
- [Configuration](#configuration)
  - [Settings and Usage](#settings-and-usage)
- [Adding Timelines and Events](#adding-timelines-and-events)
- [Installation](#installation)
  - [Requirements](#requirements) :warning:
  - [Grav Package Manager](#gpm)
  - [Manually](#manually)

![Timeline](assets/readme.png)

<a name="description"/>

## Description

The **Timeline**-plugin is for [Grav CMS](http://github.com/getgrav/grav), and lets you create and manage timelines in an ordered, hierarchical fashion. Timelines can be nested within each other, minutely customized on a page-level, and further customized with your own templates and styles. A [demo is available](https://olevik.me/staging/grav-skeleton-timeline), and demo content can be found in [/pages](https://github.com/OleVik/grav-skeleton-timeline/tree/master/pages).

<a name="configuration"/>

## Configuration

Before configuring this plugin, you should copy the `user/plugins/timeline/timeline.yaml` to `user/config/plugins/timeline.yaml` and only edit that copy.

Here is the default configuration and an explanation of available options:

```yaml
enabled: true
language: en
order:
  by: date
  dir: asc
cache: native
truncate: 100
```

<a name="settings-and-usage"/>

### Settings and Usage

| Variable | Default | Options | Note |
|----------|---------|-------------------------------------------------|--------------------------------------------------------------------------------------------|
| enabled | true | `true` or `false` | Enables or disables the plugin. |
| language | en | string (2) | Any two-letter (ISO-639-1) language code. |
| order: |  |  |  |
|   by | date | `date`, `title`, or `folder` | Orders pages according to date, title, or folder-name. |
|   dir | asc | `asc` or `desc` | Order pages ascending or descending. |
| cache | native | `native`, `persist`, `transient`, or `disabled` | Where to store plugin's internal data. |
| truncate | 100 | int or boolean | Limits the amount of words in each note, to an integer or boolean state for default (100). |

Each timeline is structured with a Header (`timeline.md`, Timeline-template) and Events (`timeline_event.md`, Timeline Event-template). Headers are used as separators and can order their descendant Events, as well as contain normal fields such as `title`, `subtitle`, and `content`. Events also render a formatted, localized `date` (using [`date_format`](http://php.net/manual/en/function.date.php) and `locale`), as well as an `image`. In addition, Events are cast as Linked Data with [JSON-LD](https://json-ld.org/), wherein `type`, `place`, `locality`, and `region` are used.

Sound confusing? It's much easier to do all this from the [Admin](https://github.com/getgrav/grav-plugin-admin)-plugin:

<a name="adding-timelines-and-events"/>

## Adding Timelines and Events

Any Page that you create in Grav with the filename `timeline.md` is the wrapper for the Timeline, and will take any Pages created with the filename `timeline_event.md` as its Events. Consider the Constantinian Dynasty, in [this folder](https://github.com/OleVik/grav-skeleton-timeline/tree/master/pages/timeline/Dominate/Constantinian). The initial [timeline.md](https://github.com/OleVik/grav-skeleton-timeline/blob/master/pages/timeline/Dominate/Constantinian/timeline.md) creates the Page at https://olevik.me/staging/grav-skeleton-timeline/timeline/dominate, and all the Pages below it are Events - each with their own [timeline_event.md](https://github.com/OleVik/grav-skeleton-timeline/blob/master/pages/timeline/Dominate/Constantinian/julian/timeline_event.md), like Julian at https://olevik.me/staging/grav-skeleton-timeline/timeline/dominate/constantinian/julian.

The plugin assumes some knowledge of basics with Grav, largely [Pages](https://learn.getgrav.org/16/content/content-pages) and [FrontMatter](https://learn.getgrav.org/16/content/headers). If you are using the Admin-plugin, you will need to create a Page using the Timeline or Timeline Event template:

1. Go to the Pages-administration:

![Pages-list in Admin](./assets/Pages-list_Grav-1.7.0_Admin-1.10.0.png)

Clicking the Add Page button yields:

![Add Page Dialog](./assets/Add_Page_Dialog.png)

#### Header Page

![Project Space](assets/header-page.png)

#### Event Page

![Project Space](assets/event-page.png)

#### Event Options

![Project Space](assets/event-options.png)

<a name="installation"/>

## Installation

Installing the Timeline-plugin can be done in one of two ways. The GPM (Grav Package Manager) installation method enables you to quickly and easily install the plugin with a simple terminal command, while the manual method enables you to do so via a zip file.

<a name="requirements"/>

### Requirements

**This plugin will only work with [Grav v1.6](https://github.com/getgrav/grav/tree/1.6) or higher, as it requires [PHP v7.1](http://php.net/manual/en/migration71.new-features.php) or higher.** Dropping this requirement would mean devolving features, which the developer is not inclined to do.

The **[intl](http://php.net/manual/en/book.intl.php)-extension for PHP must be [installed and enabled](http://php.net/manual/en/intl.installation.php "See especially User Contributed Notes")** to use this plugin.

<a name="gpm"/>

### Grav Package Manager

The simplest way to install this plugin is via the [Grav Package Manager (GPM)](http://learn.getgrav.org/advanced/grav-gpm) through your system's terminal (also called the command line). From the root of your Grav install type:

    bin/gpm install timeline

This will install the Timeline-plugin into your `/user/plugins` directory within Grav. Its files can be found under `/your/site/grav/user/plugins/timeline`.

<a name="manually"/>

### Manually

To install this plugin, just download the zip version of this repository and unzip it under `/your/site/grav/user/plugins`. Then, rename the folder to `timeline`. You can find these files on [GitHub](https://github.com/ole-vik/grav-plugin-timeline) or via [GetGrav.org](http://getgrav.org/downloads/plugins#extras).

You should now have all the plugin files under

    /your/site/grav/user/plugins/timeline
	
> NOTE: This plugin is a modular component for Grav which requires [Grav](http://github.com/getgrav/grav) and the [Error](https://github.com/getgrav/grav-plugin-error) and [Problems](https://github.com/getgrav/grav-plugin-problems) to operate.
