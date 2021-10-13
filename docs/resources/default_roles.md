---
page_title: "keycloak_default_roles Resource"
---

# keycloak\_default\_roles Resource

Allows managing default roles within Keycloak.

Roles allow you define privileges within Keycloak and map them to users and groups.

## Example Usage (Realm role)

```hcl
resource "keycloak_realm" "realm" {
  realm   = "my-realm"
  enabled = true
}

resource "keycloak_default_roles" "defalut_roles" {
  realm_id      = keycloak_realm.realm.id
  default_roles = ["uma_authorization"]
}
```

## Argument Reference

- `realm_id` - (Required) The realm this role exists within.
- `default_roles` - (Required) Realm level roles assigned to new users by default.

## Import

Default roles can be imported using the format `{{realm_id}}/{{default_role_id}}`, where `default_role_id` is the unique ID that Keycloak have to
control default roles. The ID is not easy to find in the GUI, but it appears in the dev tools when editing the default roles.

Example:

```bash
$ terraform import keycloak_default_roles.default_roles my-realm/a04c35c2-e95a-4dc5-bd32-e83a21be9e7d
```