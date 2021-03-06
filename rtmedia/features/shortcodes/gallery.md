## Gallery Shortcode


``` [rtmedia_gallery global="false" context="post" context_id="23" media_type="photo" media_author="1"] ```


## Options

### global

Default is FALSE.
If set to TRUE, context, context_id will be ignored. Only media_type value will be processed.

### context

The [context](../../developers/context.md) from which the media should be listed:

* a post_type (post, page, event, topic, reply, etc)
* a BuddyPress Component (activity, profile, group)
* a custom context, registered via code

If not provided, the current post type is assumed as the context. If BuddyPress is installed, the context is assumed to be the component on the current page. If bbPress is installed and user is on a forum, the context is set to the current topic or reply.

### context_id

* id of the current post_type (post, page, event, topic, reply, etc)
* id of the current BuddyPress Component (activity, profile, group)
* id of a custom context, registered via code

This provides the unique id of the context. For custom contexts, the database table and the id column have to be registered via code.

### media_type

1. all
2. music
3. video
4. photo
5. album

If not specified, all media types will be loaded (except albums).

### media_author

If media uploaded by a particular user needs to be displayed, set the user ID here.

### album_id

If media uploaded to a particular album needs to be displayed, set the album ID here.

### uploader

1. before : uploader on top of gallery
2. after : uploader at the end of gallery
3. true : uploader at the end of gallery (alias for after)

To show the uploader along with the gallery, use this **uploader** attribute with above values. Default is **FALSE**.

### per_page

Set this option to a value greater than 0 to override admin settings to show number of media in gallery.

### lightbox

Set this option to **FALSE**, if you have enabled **Use lightbox to display media** from rtMedia admin settings and do not want to show media of gallery shortcode in lightbox.

### media_title

Set this option to **FALSE**, if you do not want to show media title in gallery shortcode. Default value is **TRUE**.

### Some examples for your easy understanding

List out media of a perticular album_id ( Default Album ).

``` [rtmedia_gallery global=true album_id=125 sort_parameters="new,view,like,rate,comment" media_type=photo per_page=21] ```

List out media from a perticular user profile ( context_id = User_id ).

``` [rtmedia_gallery context=profile context_id=5] ```

List out media which belongs to BuddyPress group_id #1 and which are uploaded to album_id #48 ( context_id = group_id ).

``` [rtmedia_gallery context=group context_id=1 album_id=48] ```

List out media which belongs to one page ( page_id #11 ).

``` [rtmedia_gallery context=page context_id=11] ```

List out media which belongs to WordPress Album ( context_id = WordPress Album_id ).

``` [rtmedia_gallery context=dashboard context_id=248] ```

List out all the global media ( user profile / group / forum etc. ) of a perticular media author ( For example user_id = #1 ).

``` [rtmedia_gallery global=true media_author=1] ```

Note: All WordPress album has context set to **dashboard**

List out friend's media which has privacy set to 'Friend' ( contex_id = user_id of my friend, privacy = 40 ).

``` [rtmedia_gallery context=profile context_id=5 privacy=40] ```

Note: Default rtMedia **privacy levels** and their values are as follow :

1. Public : 0
2. Logged in user : 20
3. Friends : 40
4. Private : 60

## Sort Parameters *(feature of rtMedia Sorting add-on)*

By default **rtMedia Sorting** provides sort options to sort media by Title, Upload Date and Media Size. More sorting option like sort by views, likes, comments and rate has been added for media gallery rendered via gallery shortcode.

**Note:** This option is available in **rtMedia Sorting** only.

You can use `sort_parameters` parameter in gallery shortcode and can specify sort options.

Use following shortcode to provide view and like sort options:

``` [rtmedia_gallery global=true sort_parameters="view,like"] ```


Use following shortcode to provide view, like and rate sort options:

``` [rtmedia_gallery global=true sort_parameters="view,like,rate"] ```

Following are the allowed values for `sort_parameters`. Use comma separated values for multiple sort options.

1. **new:** Sort media based on Uploaded Date
2. **view:** Sort media based on Most Viewed
3. **like:** Sort media based on Most Liked
4. **comment:** Sort media based on Most Commented
5. **rate:** Sort media based on Most Rated

![sort parameters](https://cloud.githubusercontent.com/assets/7807348/6060841/92a68000-ad67-11e4-892b-378c6995cc7f.png)


## Attributes Short-Code

``` [rtmedia_gallery attribute_slug="slug-of-attribute" term_slug="terms-slug"] ```

attribute_slug: is the slug of attributes which is created or generated when you create a attribute.

term_slug: is the slug of terms which are created under the attributes. We can use a number of terms associate under the same attribute in single short-code. The terms must be comma separated.

![Selection_018](https://cloud.githubusercontent.com/assets/9261540/8003858/8f2dcbd8-0b98-11e5-8aa1-b470c5fb6f4a.png) ![Selection_017](https://cloud.githubusercontent.com/assets/9261540/8003830/60fcc4e4-0b98-11e5-9794-1e8bf96052b9.png)

As the above screenshots show, the short-code of attributes will look as follows:

``` [rtmedia_gallery attribute_slug="rtcamp" term_slug="services,product"] ```

## Favlist Short-Code

```[rtmedia_gallery favlist_id="xxx"]```

_xxx: the id of favlist which is created._

## Privacy Note

Note that the purpose of this shortcode is to provide a simpler way to display **public_galleries** of media content on your site.

For safety of your users, `rtmedia_gallery` will always fetch public content only. Some _intended_ side-effects include:

Uploads in private buddypress groups will not show even if a user can access by going to that particular buddypress-group
