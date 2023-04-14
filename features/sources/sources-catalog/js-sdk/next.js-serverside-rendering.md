---
description: >-
  Trigger an browser event when you use serverside rendering with Next.js
  framework
---

# Next.js serverside rendering

## Example of event triggered from a browser-side user interraction

Example use case : trigger a _view\_content_ event when the user scroll to 80% of the page.

```javascript
import React, { useEffect } from 'react';

const MyPage = () => {
  useEffect(() => {
    let eventTriggered = false; // Flag to track if the event has been triggered

    function handleScroll() {
      if (eventTriggered) return; // If the event has already been triggered, do nothing

      const { scrollTop, scrollHeight, clientHeight } = document.documentElement;
      if (scrollTop + clientHeight >= scrollHeight * 0.8) {
        if (window.cact) {
          window.cact('trigger', 'my_event_name', {
            myprop1: '1234',
            myprop2: 'abcd',
          }, {
            collectionDomain: "my.firstdomain.com",
            siteId: "1234", 
            sourceKey: "abcd1234",
          });
          eventTriggered = true; // Update the flag to avoid triggering the event again
        }
      }
    }

    window.addEventListener('scroll', handleScroll);

    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  }, []);

  return (
    <div>
      {/* Your server-side rendered content here */}
      <script
        dangerouslySetInnerHTML={{
          __html: `
            (function() {
              var tc = document.createElement('script');
              tc.type = 'text/javascript';
              tc.async = true;
              tc.src = 'https://cdn.tagcommander.com/events/sdk.js';
              var s = document.getElementsByTagName('script')[0];
              s.parentNode.insertBefore(tc, s);
            })();
          `
        }}
      />
    </div>
  );
};

export default MyPage;
```
