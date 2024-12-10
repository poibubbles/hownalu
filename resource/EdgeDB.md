Try oauthdebugger.com? oidcdebugger.com?
### New local user/role

As of 2024-11-10 "Currently, the `superuser` qualifier is mandatory, i.e. it is not possible to create non-superuser roles for now." https://docs.edgedb.com/database/reference/admin/roles#role :

		create superuser role <name> {
			set password := '<password>';
		};

		select sys::Role.name;
		select sys::Role {name, is_superuser};

Log in using `edgedb -I <instance> --user <username> --password`  # wait for prompt.

### Recon

`edgedb info`
`edgedb instance list --extended`
`edgedb server info --latest`
`edgedb instance credentials` (run in instance directory with `edgedb.toml` or include `-H`, `-P`, `-I` connection info)

Credentials in `EDGEDB_CREDENTIALS_FILE` or `<Config>/credentials/<instance>.json`.

### Working

`edgedb migration create`
`edgedb migrate`
`edgedb list types`


### Configuration

https://docs.edgedb.com/database/reference/admin/configure

### Authn via HTTP

https://docs.edgedb.com/libraries/http#ref-http-auth for v4.0+.
