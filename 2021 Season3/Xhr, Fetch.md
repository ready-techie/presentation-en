
# Form

```jsx
<form> 
	<input type=text value='Text1'>
	<input type=text value='Text2'>
	<input type=submit>
</form>
```

When the existing web application was `submitted` to the web server, the web server processed the data according to the requested content, wrote it as a new web page, and returned to the response.

**In other words**, in order to receive data from the server unconditionally, refresh should have been performed.

Then, in 1999, XHR, which asynchronously imports data, appears.

# XHR (XML HTTP Request)

```jsx
let xhr = new XMLHttpRequest();
xhr.open('GET', 'https://jsonplaceholder.typicode.com/todos/1');

// request state change event
xhr.onreadystatechange = function() {

  // request completed?
  if (xhr.readyState !== 4) return;

  if (xhr.status === 200) {
    // request successful - show response
    console.log(xhr.responseText);
  }
  else {
    // request error
    console.log('HTTP error', xhr.status, xhr.statusText);
  }
};

// start request
xhr.send();

------- console --------- 

{
  "userId": 1,
  "id": 1,
  "title": "delectus aut autem",
  "completed": false
}
```

`XMLHttpRequest` (XHR) objects are used to interact with servers. You can retrieve data from a URL without having to do a full page refresh. This enables a Web page to update just part of a page without disrupting what the user is doing.

`XMLHttpRequest` is used heavily in [AJAX](https://developer.mozilla.org/en-US/docs/Web/Guide/AJAX) programming.

After the client requests and receives only the necessary data from the web server, the client may process the data.

- Reduce the waste of bandwidth.
- Interaction with users.

## AJAX(Asynchronous Javascript And XML)

In 2006, Google gave a new name AJAX (Asynchronous Javascript And XML)

## jquery.ajax()

```jsx
//jquery GET request

$.ajax({
  url,
  method: "GET",
  dataType: "json"
})
  .done(json => {
    console.log(json);
  })
  .fail((xhr, status, errorThrown) => {})
  .always((xhr, status) => {
    console.log(xhr.responseText);
  });
```

# Fetch

```jsx
//fetch GET request

fetch(`${url}?${querystring}`)
  .then(result => result.json())
  .then(result => {
    console.log(result);
  })
  .catch(err => {
    console.log(err);
  });
```

# Axios

```jsx
//axios GET request
axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  })
  .then(function () {
    // always executed
  });

```

Promise based HTTP client for the browser and node.js

**Pros**

- Highly compatible with cross-browsing
- Old browser support.

**Cons** 

- Need to library import

[https://ko.wikipedia.org/wiki/Ajax#기존_기술과의_차이점](https://ko.wikipedia.org/wiki/Ajax#%EA%B8%B0%EC%A1%B4_%EA%B8%B0%EC%88%A0%EA%B3%BC%EC%9D%98_%EC%B0%A8%EC%9D%B4%EC%A0%90)

[https://velog.io/@04_miffy/form-XHR-AJAX-jQuery.ajax-Fetch](https://velog.io/@04_miffy/form-XHR-AJAX-jQuery.ajax-Fetch)

[https://stackoverflow.com/questions/35549547/fetch-api-vs-xmlhttprequest](https://stackoverflow.com/questions/35549547/fetch-api-vs-xmlhttprequest)