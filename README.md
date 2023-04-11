# cors-proxy
This allows you to bypass CORS protocol.

An example use case would be using it to get an image from a CORS protected image, such as given in the test folder, or as shown below:

```js
      const imageUrl = "https://scontent-lax3-1.cdninstagram.com/v/t51.2885-19/119949251_1555425461304551_8942171633550168648_n.jpg?stp=dst-jpg_s150x150&_nc_ht=scontent-lax3-1.cdninstagram.com&_nc_cat=1&_nc_ohc=vwiU5kfsjkQAX80xVoq&edm=AEF8tYYBAAAA&ccb=7-5&oh=00_AfB3qa6djWPIrqYy78raJXl5mbGn2ArpYPd3--HTKfGyag&oe=64390002&_nc_sid=a9513d"; // URL of the blocked image
      const corsAnywhereUrl = "https://aco-proxy.cyclic.app/"; // URL of your CORS Anywhere server

      fetch(corsAnywhereUrl + imageUrl)
        .then((response) => {
          if (response.ok) {
            // Response is successful, get the image data
            return response.blob();
          } else {
            throw new Error("Failed to load image");
          }
        })
        .then((blob) => {
          // Create an object URL from the blob
          const objectUrl = URL.createObjectURL(blob);

          // Use the object URL to display the image
          const img = new Image();
          img.src = objectUrl;
          document.body.appendChild(img);
        })
        .catch((error) => {
          console.error(error);
        });
 ```
 
 Feel free to use the one I have hosted live at `https://aco-proxy.cyclic.app/`. WIth your frontend, you can use it to do requests bypassing the CORS policy.
 
 For an example, if you were to fetch something at `https://my-api.com/get-user/4`, you'd call a GET request with `fetch` to `https://aco-proxy.cyclic.app/https://my-api.com/get-user/4`.
 
 Have fun using it!
