# cacher

A utility to run Python scripts with persistent, fully-cached HTTP(S) requests.

**Key Features:**

*   **Persistent Caching:** Caches all HTTP requests to disk.  Never re-requests based on age.
*   **Customizable Cache Directory:** Specify a custom location for the cache.
*   **Cache Listing:**  List all cached requests with URLs and request bodies.
*   **Drop-in Replacement:**  Wraps `requests` to seamlessly enable caching within your scripts.
*   **Supports GET/DELETE/POST/PUT**

**Usage:**

```bash
cacher --list --cache-dir <path>
cacher ( command to run )
```

**Dependencies:**

*   Python >= 3.8
*   `requests`
*   `rich`
*   `requests_cache`
*   `typer`

These will be automatically installed if missing.

**How it Works:**

The script redefines `requests.Session` to a custom class `FullyCachedSession`. This class caches all HTTP requests made using the `requests` library to the specified cache directory. It does this very conservatively to make sure runs are deterministic.

