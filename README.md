# URL-SHORTENER

import hashlib

# Simulated database
url_db = {}

def shorten_url(long_url):
    # Create a short hash of the URL
    hash_object = hashlib.md5(long_url.encode())
    short_hash = hash_object.hexdigest()[:6]
    
    short_url = f"http://short.url/{short_hash}"
    url_db[short_url] = long_url
    return short_url

def expand_url(short_url):
    return url_db.get(short_url, "URL not found")

# Example usage
if __name__ == "__main__":
    long_url = "https://www.example.com/some/very/long/url"
    short_url = shorten_url(long_url)
    print("Shortened:", short_url)
    
    original_url = expand_url(short_url)
    print("Expanded:", original_url)
