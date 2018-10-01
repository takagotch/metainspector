### metainspector
---

https://github.com/jaimeiniesta/metainspector

```
gem install metainspector
gem 'metainspector'

```

```ruby
page = MetaInspector.new('http://sitevalidator.com')
page = MetaInspector.new('sitevalidator.com')
page = MetaInspector.new('http://sitevalidator.com')
page.response.status
page.reponse.headers

page.url
page.tracked?
page.untracked_url
page.untrack!
page.scheme
page.host
page.root_url

page.head_links
page.stylesheets
page.canonicals
page.feed

page.title
page.best_title
page.author
page.best_author
page.description
page.best_description

page.links.raw
page.links.all
page.links.http
page.links.on_http
page.links.interal
page.links.external

page.images
page.images.with_size
page.images.best
page.images.favicon

page.meta_tags
  'name' => {
    'keywords' => ['one, two, three'],
    'description' => ['the description'],
    'author' => ['tky Takagotch'],
    'robots' => ['index,follow'],
    'revisit' => ['15 days'],
    'dc.date.issued' => ['2018-01-01']
  },
  'http-equiv' => {
    'content-type' => ['text/html; charset=UTF-8'],
    'content-style-type' => ['text/css']
  },
  'property' => {
    'og:title' => ['An OG title'],
    'og:type' => ['website'],
    'og:url' => ['http://ex.com/meta-tags'],
    'og:image' => ['http://ex.com/rock.jpg',
                   'http://ex.com/rock2.jpg',
                   'http://ex.com/rock3.jpg'],
    'og:image:width' => ['300'],
    'og:image:height' => ['300', '1000']
    'charset' => {'UTF-8'}
  }

page.meta_tag['property']
page.meta_tag['name']
page.meta_tag['name']['keywords']
page.meta
page.meta['author']

page.charset
page.content_type
page.to_hash "title" => { "MarkupValdator :: site-wide markup validation tool", ... }
page.to_s
page.parsed

page = MetaInspector.new(url, :encoding => 'UTF-8')
page = MetaInspector.new('www.google', :connection_timeout => 10, :read_timeout => 5, :retroes => 4)

begin
  page = MetaInspector.new(url)
rescue MetaInspector::TimeoutError
  enqueue_for_future_fetch_attempt(url)
  render_simple(url)
else
  render_rich(page)
end

page = MetaInspector.new('facebook.com', :allow_redirections => false)

{
  'User-Agent' => "MetaInspector/#{MetaInsepctor::VERSION} (+https://github.com/jaimeiniesta/metainspector)"
  'Accept-Encoding' => 'identity'
}

page = MetaInspector.new('ex.com', :headers => {'User-Agent' => 'My custom User-Agent'})

MetaInspector.new('http://ex.com')
MetaInspector.new('https://ex.com', faraday_options: { ssl: { verify: false } } )

page = MetaInspector.new('', :allow_non_html_content => true)

page = MetaInspector.new('http://ex.com/image.png')
page.content_type
page.description
page = MetaInspector.new('http://ex.com/image.png', :allow_non_html_content => true)
page.content_type
page.description

page = MetaInspector.new('sitevalidator.com')
page.url
page = MetaInspector.new('http://www.III.com')
page.url

page = MetaInspector.new('http://ex.com', download_images: false)
cache = ActiveSupport::Cache.lookup_store(:file_store, '/tmp/cache')
page = MetaInspector.new('http://ex.com', faraday_http_cache: { store: cache })
```
```
irb
page = MetaInspector.new('http://sitevalidator.com')
page.title
page.meta['description']
page.meta['keywords']
page.links.size
page.links[4]

```
