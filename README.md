# ocaml-cordova-plugin-device

Binding to
[cordova-plugin-device](https://github.com/apache/cordova-plugin-device)

[Example
application](https://github.com/dannywillems/ocaml-cordova-plugin-device-example).

## What does cordova-plugin-device do ?

```
This plugin defines a global device object, which describes the device's
hardware and software. Although the object is in the global scope, it is not
available until after the deviceready event.
```

Source: [cordova-plugin-device](https://github.com/apache/cordova-plugin-device)

## Repository branches and tags

We are migrating bindings from
[js_of_ocaml](https://github.com/ocsigen/js_of_ocaml) (low level bindings) to
[gen_js_api](https://github.com/lexifi/gen_js_api) (high level bindings).

The gen_js_api binding allows to use *pure* ocaml types (you don't have to use
the ## syntax from js_of_ocaml or Js.string type but only # and string type).

The js_of_ocaml version is available in the branch
[*js_of_ocaml*](https://github.com/dannywillems/ocaml-cordova-plugin-device/tree/js_of_ocaml)
but we **recommend** to use the gen_js_api version which is the master branch.

## How to use ?

See the official documentation
[cordova-plugin-device](https://github.com/apache/cordova-plugin-device)

## ! BE CAREFUL !

The device plugin creates a new object called *device*, but the object is
available when the *deviceready* event is handled.

We provide a function Device.t of type unit -> device which does returns the
*device* object. You need to call it when the deviceready event is handled, eg
(with js_of_ocaml)

```OCaml
let on_device_ready _ =
  let d = Device.t () in
  (* Some code *)

let _ =
  Dom.addEventListener Dom_html.document (Dom.Event.make "deviceready")
  (Dom_html.handler on_device_ready) Js._false
```
