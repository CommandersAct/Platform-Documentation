# Permanent properties

The setProperty method allows you to set persistent properties that are automatically added to all events sent by the Commanders Act Web SDK.

```
cact('setProperty', 'property_name', 'property_value');
```

Usage example:

```
cact('setProperty', 'page_type', 'homepage');
cact('setProperty', 'user.email', 'mymail@gmail.com');
cact('setProperty', 'user.firstname', 'Jim');

cact('trigger', 'page_view', {
  url: 'https://toto.fr',
  user: {
    phone: '0123456',
  },
});
```

will returns the following result

```
{
  page_type: 'homepage',
  url: 'https://toto.fr',
  user: {
    email: 'mymail@gmail.com',
    firstname: 'Jim',
    phone: '0123456',
  },
}
```
