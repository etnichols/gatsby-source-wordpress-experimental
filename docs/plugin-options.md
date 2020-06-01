# Plugin Options

- [url](#url-string)

- [verbose](#verbose-boolean)

- [debug](#debug-object)
- [debug.graphql](#debug.graphql-object)
    - [debug.graphql.showQueryVarsOnError](#debug.graphql.showqueryvarsonerror-boolean)
    - [debug.graphql.panicOnError](#debug.graphql.paniconerror-boolean)
    - [debug.graphql.onlyReportCriticalErrors](#debug.graphql.onlyreportcriticalerrors-boolean)
    - [debug.graphql.writeQueriesToDisk](#debug.graphql.writequeriestodisk-boolean)
  
- [develop](#develop-object)
- [develop.nodeUpdateInterval](#develop.nodeupdateinterval-int)
  - [develop.hardCacheMediaFiles](#develop.hardcachemediafiles-boolean)
  
- [auth](#auth-object)
- [auth.htaccess](#auth.htaccess-object)
    - [auth.htaccess.username](#auth.htaccess.username-string)
    - [auth.htaccess.password](#auth.htaccess.password-string)
  
- [schema](#schema-object)
- [schema.typePrefix](#schema.typeprefix-string)
  - [schema.timeout](#schema.timeout-int)
  - [schema.perPage](#schema.perpage-int)
  
- [excludeFieldNames](#excludefieldnames-array)

- [html](#html-object)
- [html.useGatsbyImage](#html.usegatsbyimage-boolean)
  - [html.imageMaxWidth](#html.imagemaxwidth-int)
  - [html.fallbackImageMaxWidth](#html.fallbackimagemaxwidth-int)
  - [html.imageQuality](#html.imagequality-int)
  
- [type](#type-object)
- [type[TypeName].exclude](#typetypename.exclude-boolean)
  
- [type[TypeName].excludeFieldNames](#typetypename.excludefieldnames-array)
  
- [type.\_\_all](#type.__all-object)
  
- [type.RootQuery](#type.rootquery-object)
  
- [type.MediaItem.lazyNodes](#type.mediaitem.lazynodes-boolean)



## url: String

This is the only plugin option which is required for the plugin to work properly.

This should be the full url of your GraphQL endpoint.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
    url: `https://yoursite.com/graphql`
  },
},
```



## verbose: Boolean

Wether there will be verbose output in the terminal. Set true for verbose. Default is `false`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		verbose: true,
  },
},
```



## debug: Object

An object which contains options related to debugging. See below for options.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
  	debug: {

    },
  },
},
```



### debug.graphql: Object

An object which contains GraphQL debugging options. See below for options.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		debug: {
      graphql: {

      },
    },
  },
},
```



#### debug.graphql.showQueryVarsOnError: Boolean

When a GraphQL error is returned and the process exits, this plugin option determines wether or not to log out the query vars that were used in the query that returned GraphQL errors. Default is false.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		debug: {
      graphql: {
      	showQueryVarsOnError: true,
      },
    },
  },
},
```



#### debug.graphql.panicOnError: Boolean

Determines wether or not to panic when any GraphQL error is returned.

Default is false because sometimes non-critical errors are returned alongside valid data.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		debug: {
      graphql: {
      	panicOnError: false,
      },
    },
  },
},
```



#### debug.graphql.onlyReportCriticalErrors: Boolean

Determines wether or not to log non-critical errors. A non-critical error is any error which is returned alongside valid data. In previous versions of WPGraphQL this was very noisy because trying to access an entity that was private returned errors. Default is true.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		debug: {
      graphql: {
      	onlyReportCriticalErrors: true,
      },
    },
  },
},
```



#### debug.graphql.writeQueriesToDisk: Boolean

When true, all internal GraphQL queries generated during node sourcing will be written out to `./WordPress/GraphQL/[TypeName]/*.graphql` for every type that is sourced. This is very useful for debugging GraphQL errors. Default is false.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		debug: {
      graphql: {
      	writeQueriesToDisk: true,
      },
    },
  },
},
```



## develop: Object

Options related to the `gatsby develop` process.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		develop: {
      // options related to `gatsby develop`
    },
  },
},
```



### develop.nodeUpdateInterval: Int

Specifies in milliseconds how often Gatsby will ask WP if data has changed during development. If you want to see data update in near-realtime while you're developing, set this low. Your server may have trouble responding to too many requests over a long period of time and in that case, set this high. Setting it higher saves electricity too ⚡️🌲

Default is `300`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		develop: {
      nodeUpdateInterval: 300
    },
  },
},
```



### develop.hardCacheMediaFiles: Boolean

When true, media files will be hard-cached outside the Gatsby cache in a `./.wordpress-cache/path/to/media/file.jpeg` . This is useful for preventing media files from being re-downloaded when the Gatsby cache automatically clears.

Default is false.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		develop: {
      hardCacheMediaFiles: true,
    },
  },
},
```



## auth: Object

Options related to authentication. See below for options.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		auth: {

    },
  },
},
```



### auth.htaccess: Object

Options related to  htaccess authentication. See below for options.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		auth: {
      htaccess: {

      },
    },
  },
},
```



#### auth.htaccess.username: String

The username for your .htpassword protected site.

Default is `null`

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		auth: {
      htaccess: {
        username: `admin`,
      },
    },
  },
},
```



#### auth.htaccess.password: String

The password for your .htpassword protected site.

Default is `null`

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		auth: {
      htaccess: {
        password: `1234strong_password`,
      },
    },
  },
},
```



## schema: Object

Options related to fetching and ingesting the remote schema. See below for options.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		schema: {

    },
  },
},
```



### schema.typePrefix: String

The prefix for all ingested types from the remote schema. For example `Post` becomes `WpPost`.

Default is `Wp` .

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		schema: {
      typePrefix: `Wp`,
    },
  },
},
```



### schema.timeout: Int

The amount of time in ms before GraphQL requests will time out.

Default is `30 * 1000 // 30 seconds`

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		schema: {
      timeout: 30000,
    },
  },
},
```



### schema.perPage: Int

The number of nodes to fetch per page during node sourcing.

Default is `100`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		schema: {
      perPage: 100,
    },
  },
},
```



## excludeFieldNames: Array

A list of field names to globally exclude from the ingested schema.

Default is `[]`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		excludeFieldNames: [`viewer`],
  },
},
```



## html: Object

Options related to html field processing. See below for options.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		html: {

    },
  },
},
```



### html.useGatsbyImage: Boolean

Causes the source plugin to find/replace images in html with Gatsby images.

Default is `true`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		html: {
      useGatsbyImage: true,
    },
  },
},
```



### html.imageMaxWidth: Int

Adds a limit to the max width an image can be.
If the image size selected in WP is smaller or the image file width is smaller than this
those values will be used instead.

Default is `null`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		html: {
      imageMaxWidth: 1024,
    },
  },
},
```



### html.fallbackImageMaxWidth: Int

If a max width can't be inferred from html this value will be passed to Sharp.

If the image is smaller than this, the image file's width will be used instead.

Default is `100`. @todo this is too low..

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		html: {
      fallbackImageMaxWidth: 800,
    },
  },
},
```



### html.imageQuality: Int

Determines the image quality that Sharp will use when generating inline html image thumbnails.

Default is `90`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		html: {
      imageQuality: 90,
    },
  },
},
```



## type: Object

Options related to specific types in the remote schema. See below for options.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		type: {

    },
  },
},
```



### type[TypeName].exclude: Boolean

Completely excludes a type from node sourcing and from the ingested schema.

Default is `undefined`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		type: {
      Page: {
        exclude: true,
      },
    },
  },
},
```



### type[TypeName].excludeFieldNames: Array

Excludes fields on a type by field name. Default is `undefined`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		type: {
      Page: {
        excludeFieldNames: [`dateGmt`, `parent`],
      },
    },
  },
},
```



### type.\_\_all: Object

A special type setting which is applied to all types in the ingested schema. It can take the same options as regular types.

Default is `undefined`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		type: {
      __all: {
        limit: 10,
      },
    },
  },
},
```



### type.RootQuery: Object

A special type which is applied to any non-node root fields that are ingested and stored under the root `wp` field. It accepts the same options as other types.

Default is `{ excludeFieldNames: ['viewer', 'node', 'schemaMd5'], },`

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		type: {
      RootQuery: {
        excludeFieldNames: [`viewer`]
      },
    },
  },
},
```



### type.MediaItem.lazyNodes: Boolean

Enables a different media item sourcing strategy. Instead of fetching Media Items that are referenced by other nodes, Media Items will be fetched in connection resolvers from other nodes. This may be desireable if you're not using all of the connected images in your WP instance. This is not currently recommended because it messes up cli output and can be slow due to query running concurrency.

Default is `false`.

```js
{
  resolve: `gatsby-source-wordpress-experimental`,
	options: {
		type: {
      MediaItem: {
        lazyNodes: true,
      },
    },
  },
},
```





# Up Next :point_right:

- :boat: [Migrating from other WP source plugins](./migrating-from-other-wp-source-plugins.md)
- :house: [Hosting](./hosting.md)
- :athletic_shoe: [Themes, Starters, and Examples](./themes-starters-examples.md)
- :medal_sports: [Usage with popular WPGraphQL extensions](./usage-with-popular-wp-graphql-extensions.md)
- :gear: [How does this plugin work?](./how-does-this-plugin-work.md)
- :hammer_and_wrench: [Debugging and troubleshooting](./debugging-and-troubleshooting.md)
- :national_park: [Community and Support](./community-and-support.md)
- :point_left: [Back to README.md](../README.md)