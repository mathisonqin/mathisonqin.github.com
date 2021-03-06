---
layout: post
title: "code style"
description: ""
category: example
tags: [code style, example]
---
{% include JB/setup %}
here is code:
## google-code-prettify

<pre class="prettyprint linenums">
static ngx_int_t
ngx_add_inherited_sockets(ngx_cycle_t *cycle)
{
    u_char           *p, *v, *inherited;
    ngx_int_t         s;
    ngx_listening_t  *ls;

    inherited = (u_char *) getenv(NGINX_VAR);

    if (inherited == NULL) {
        return NGX_OK;

}

ngx_log_error(NGX_LOG_NOTICE, cycle->log, 0,
        "using inherited sockets from \"%s\"", inherited);

if (ngx_array_init(&cycle->listening, cycle->pool, 10,
            sizeof(ngx_listening_t))
        != NGX_OK)
{
    return NGX_ERROR;

}

for (p = inherited, v = p; *p; p++) {
    if (*p == ':' || *p == ';') {
        s = ngx_atoi(v, p - v);
        if (s == NGX_ERROR) {
            ngx_log_error(NGX_LOG_EMERG, cycle->log, 0,
                    "invalid socket number \"%s\" in " NGINX_VAR
                    " environment variable, ignoring the rest"
                    " of the variable", v);
            break;

        }

        v = p + 1;

        ls = ngx_array_push(&cycle->listening);
        if (ls == NULL) {
            return NGX_ERROR;

        }

        ngx_memzero(ls, sizeof(ngx_listening_t));

        ls->fd = (ngx_socket_t) s;

    }

}

ngx_inherited = 1;

return ngx_set_inherited_sockets(cycle);

}
</pre>

## pygments
{% highlight c %}
static ngx_int_t
ngx_add_inherited_sockets(ngx_cycle_t *cycle)
{
    u_char           *p, *v, *inherited;
    ngx_int_t         s;
    ngx_listening_t  *ls;

    inherited = (u_char *) getenv(NGINX_VAR);

    if (inherited == NULL) {
        return NGX_OK;

}

ngx_log_error(NGX_LOG_NOTICE, cycle->log, 0,
        "using inherited sockets from \"%s\"", inherited);

if (ngx_array_init(&cycle->listening, cycle->pool, 10,
            sizeof(ngx_listening_t))
        != NGX_OK)
{
    return NGX_ERROR;

}

for (p = inherited, v = p; *p; p++) {
    if (*p == ':' || *p == ';') {
        s = ngx_atoi(v, p - v);
        if (s == NGX_ERROR) {
            ngx_log_error(NGX_LOG_EMERG, cycle->log, 0,
                    "invalid socket number \"%s\" in " NGINX_VAR
                    " environment variable, ignoring the rest"
                    " of the variable", v);
            break;

        }

        v = p + 1;

        ls = ngx_array_push(&cycle->listening);
        if (ls == NULL) {
            return NGX_ERROR;

        }

        ngx_memzero(ls, sizeof(ngx_listening_t));

        ls->fd = (ngx_socket_t) s;

    }

}

ngx_inherited = 1;

return ngx_set_inherited_sockets(cycle);

}
{% endhighlight %}
