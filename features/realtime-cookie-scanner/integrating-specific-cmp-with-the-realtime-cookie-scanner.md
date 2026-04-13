# Integrating specific CMP with the Realtime Cookie Scanner (closed beta)

### Natively supported CMPs

The Realtime Cookie Scanner natively supports the following CMPs:

* Didomi
* OneTrust
* Commanders Act (privacy module)

If you are using one of these CMPs, no additional configuration is required. You can stop here.

***

### Using a non-supported CMP

If your CMP is not listed above, you can still integrate it very easily.

You only need to inform the scanner about the current consent status by calling a JavaScript function.

***

## Simple integration

Call this function with the current consent status:

```
cact('cookieScanner.updateConsent', {
  status: 'optout'
});
```

***

### When to call this function

You must call it:

* once, as soon as you know the consent status on the page
* then every time the consent status changes

***

### Possible values for `status`

Use only these 4 values:

* `unset` → no choice has been made yet
* `optin` → all optional cookies are accepted
* `optout` → all optional cookies are refused
* `mixed` → some categories are accepted, others are not

***

### How to choose the correct status

If your CMP manages multiple categories (analytics, advertising, etc.), use this simple rule:

* everything accepted → `optin`
* everything refused → `optout`
* partially accepted → `mixed`
* no choice yet → `unset`

The status must always reflect the **actual consent state in your CMP**.

***

### Simple example

#### On page load

If the user has not made a choice yet:

```
cact('cookieScanner.updateConsent', {
  status: 'unset'
});
```

***

#### If the user refuses

```
cact('cookieScanner.updateConsent', {
  status: 'optout'
});
```

***

#### If the user accepts everything

```
cact('cookieScanner.updateConsent', {
  status: 'optin'
});
```

***

#### If the user selects specific categories

```
cact('cookieScanner.updateConsent', {
  status: 'mixed'
});
```

***

### Important

* always use the real consent status
* call the function on page load
* call it every time the consent changes

***

### Good to know

* nothing else is required
* no specific CMP integration is needed
* the function can be called before or after the scanner is loaded

***

## Summary

You only need to:

1. read the consent status from your CMP
2. call:

```
cact('cookieScanner.updateConsent', { status: '...' });
```

3. call it again whenever the consent changes

***

If you follow these steps, your CMP will be correctly handled by the Realtime Cookie Scanner.
