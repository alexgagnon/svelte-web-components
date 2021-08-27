<svelte:options tag='custom-input'></svelte:options>

<script lang="ts">
  export let id: string;
  export let name: string | undefined = undefined;
  export let type: 'text' | 'password' = 'text';
  export let label: string | undefined = undefined;

  $: computedName = name || id;

  // example of properties required:
  let _hello;
  // static formAssociated = true
  get hello() {return _hello;}
  set hello(value) {_hello = value;}


  // TODO: this needs to be the output, somehow?
  // class Input extends HTMLElement {
  //   static formAssociated = true;

  //   constructor() {
  //     super();
  //     // Get access to the internal form control APIs
  //     this.internals_ = this.attachInternals();
  //     // internal value for this control
  //     this.value_ = 0;
  //   }

  //   // Form controls usually expose a "value" property
  //   get value() { return this.value_; }
  //   set value(v) { this.value_ = v; }

  //   // The following properties and methods aren't strictly required,
  //   // but browser-level form controls provide them. Providing them helps
  //   // ensure consistency with browser-provided controls.
  //   get form() { return this.internals_.form; }
  //   get name() { return this.getAttribute('name'); }
  //   get type() { return this.localName; }
  //   get validity() {return this.internals_.validity; }
  //   get validationMessage() {return this.internals_.validationMessage; }
  //   get willValidate() {return this.internals_.willValidate; }

  //   checkValidity() { return this.internals_.checkValidity(); }
  //   reportValidity() {return this.internals_.reportValidity(); }
  // }
</script>

<div class='form-group'>
  <slot name='prefix'></slot>
  <input {id} {type} name={computedName} />
  <label for={id}><slot name='label'>{label}</slot></label>
  <slot name='suffix'></slot>
</div>