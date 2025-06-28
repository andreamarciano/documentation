# 📝 Forms

Bootstrap offers a full suite of form components and layout tools to build modern, responsive, and accessible forms with minimal effort.

---

## 📚 Table of Contents

1. [Form Control](#️-form-control)
2. [Selects](#-selects)
3. [Checkboxes & Radios](#-checkboxes--radios)
4. [Range Inputs](#️-range-inputs)
5. [Input Groups](#-input-groups)
6. [Floating Labels](#-floating-labels)
7. [Form Layout](#-form-layout)
8. [Validation](#-validation)
9. [Full Form Example](#full-form-example)

---

## ✏️ Form Control

Use `.form-control` to style basic text inputs, textareas, and more:

```tsx
<input type="text" className="form-control" placeholder="Enter your name" />

<textarea className="form-control" rows={4}></textarea>
```

> ✅ Automatically applies consistent padding, border, and focus styles.

---

## 🔽 Selects

Use `.form-select` for dropdowns:

```tsx
<select className="form-select">
  <option selected>Select a country</option>
  <option value="1">Italy</option>
  <option value="2">Germany</option>
</select>
```

> 🎯 You can also use `multiple` or size attributes for customization.

---

## ✅ Checkboxes & Radios

Use `.form-check` to style checkboxes and radio buttons.

### Checkbox

```tsx
<div className="form-check">
  <input className="form-check-input" type="checkbox" id="check1" />
  <label className="form-check-label" htmlFor="check1">
    Accept terms
  </label>
</div>
```

### Radio

```tsx
<div className="form-check">
  <input className="form-check-input" type="radio" name="choice" id="opt1" />
  <label className="form-check-label" htmlFor="opt1">
    Option 1
  </label>
</div>
```

---

## 🎚️ Range Inputs

Use `.form-range` for slider inputs:

```tsx
<input type="range" className="form-range" min="0" max="100" />
```

> 💡 You can pair this with output elements or tooltips for better UX.

---

## 🔗 Input Groups

Use `.input-group` to group inputs with text or buttons:

```tsx
<div className="input-group">
  <span className="input-group-text">@</span>
  <input type="text" className="form-control" placeholder="Username" />
</div>
```

Or with buttons:

```tsx
<div className="input-group">
  <input type="text" className="form-control" placeholder="Search" />
  <button className="btn btn-outline-secondary" type="button">Go</button>
</div>
```

---

## 🧷 Floating Labels

Use `.form-floating` to display labels as placeholders that float above the field on focus:

```tsx
<div className="form-floating">
  <input type="email" className="form-control" id="email" placeholder="name@example.com" />
  <label htmlFor="email">Email address</label>
</div>
```

> ⚠️ Inputs must include a `placeholder` (even empty) for this to work.

---

## 🧱 Form Layout

Bootstrap supports flexible form layouts using the grid system or flex utilities.

### Grid-based layout

```tsx
<div className="row g-3">
  <div className="col-md-6">
    <input type="text" className="form-control" placeholder="First name" />
  </div>
  <div className="col-md-6">
    <input type="text" className="form-control" placeholder="Last name" />
  </div>
</div>
```

### Horizontal layout

```tsx
<div className="row mb-3">
  <label htmlFor="inputEmail" className="col-sm-2 col-form-label">Email</label>
  <div className="col-sm-10">
    <input type="email" className="form-control" id="inputEmail" />
  </div>
</div>
```

---

## ✅ Validation

Bootstrap provides **client-side validation styles** using native HTML validation APIs and utility classes.

```tsx
<form className="needs-validation" noValidate>
  <div className="mb-3">
    <input type="text" className="form-control is-valid" required />
    <div className="valid-feedback">Looks good!</div>
  </div>

  <div className="mb-3">
    <input type="email" className="form-control is-invalid" required />
    <div className="invalid-feedback">Please enter a valid email.</div>
  </div>
</form>
```

> 🧪 You must add `noValidate` and handle validation manually (e.g., on submit) if you're working with React.

---

## Full Form Example

```tsx
<form className="container mt-4 needs-validation" noValidate>
  <div className="row g-3">
    {/* First Name */}
    <div className="col-md-6">
      <label htmlFor="firstName" className="form-label">First Name</label>
      <input type="text" className="form-control" id="firstName" required />
      <div className="invalid-feedback">First name is required.</div>
    </div>

    {/* Last Name */}
    <div className="col-md-6">
      <label htmlFor="lastName" className="form-label">Last Name</label>
      <input type="text" className="form-control" id="lastName" required />
      <div className="invalid-feedback">Last name is required.</div>
    </div>

    {/* Email */}
    <div className="col-md-6">
      <label htmlFor="email" className="form-label">Email</label>
      <input type="email" className="form-control" id="email" required />
      <div className="invalid-feedback">Please enter a valid email.</div>
    </div>

    {/* Password */}
    <div className="col-md-6">
      <label htmlFor="password" className="form-label">Password</label>
      <input type="password" className="form-control" id="password" required minLength={6} />
      <div className="invalid-feedback">Password must be at least 6 characters.</div>
    </div>

    {/* Gender (Radio) */}
    <div className="col-12">
      <label className="form-label d-block mb-1">Gender</label>
      <div className="form-check form-check-inline">
        <input className="form-check-input" type="radio" name="gender" id="male" required />
        <label className="form-check-label" htmlFor="male">Male</label>
      </div>
      <div className="form-check form-check-inline">
        <input className="form-check-input" type="radio" name="gender" id="female" />
        <label className="form-check-label" htmlFor="female">Female</label>
      </div>
      <div className="form-check form-check-inline">
        <input className="form-check-input" type="radio" name="gender" id="other" />
        <label className="form-check-label" htmlFor="other">Other</label>
      </div>
    </div>

    {/* Country (Select) */}
    <div className="col-md-6">
      <label htmlFor="country" className="form-label">Country</label>
      <select className="form-select" id="country" required>
        <option value="">Choose...</option>
        <option>Italy</option>
        <option>Germany</option>
        <option>USA</option>
      </select>
      <div className="invalid-feedback">Please select a country.</div>
    </div>

    {/* Floating Label (Username) */}
    <div className="col-md-6">
      <div className="form-floating">
        <input type="text" className="form-control" id="username" placeholder="Username" />
        <label htmlFor="username">Username</label>
      </div>
    </div>

    {/* Range Input */}
    <div className="col-12">
      <label htmlFor="experience" className="form-label">Years of Experience: <strong id="years">2</strong></label>
      <input type="range" className="form-range" min="0" max="10" step="1" id="experience" />
    </div>

    {/* Input Group (Website) */}
    <div className="col-12">
      <label htmlFor="website" className="form-label">Your Website</label>
      <div className="input-group">
        <span className="input-group-text">https://</span>
        <input type="text" className="form-control" id="website" placeholder="yourdomain.com" />
      </div>
    </div>

    {/* Checkbox */}
    <div className="col-12">
      <div className="form-check">
        <input className="form-check-input" type="checkbox" id="agree" required />
        <label className="form-check-label" htmlFor="agree">
          I agree to the terms and conditions
        </label>
        <div className="invalid-feedback">You must agree before submitting.</div>
      </div>
    </div>

    {/* Submit Button */}
    <div className="col-12">
      <button className="btn btn-primary w-100" type="submit">Submit Form</button>
    </div>
  </div>
</form>
```
