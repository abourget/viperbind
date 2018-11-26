# viperbind

`viperbind` auto-binds viper variables to cobra flags, and adds
support for environment variables without requiring the tedious
bindings.

It maps:

* `program dothis --flag` -> `PREFIX_DOTHIS_CMD_FLAG`
* `program --threads=5 dothat thenthis` -> `PREFIX_GLOBAL_THREADS`
* `program dothat thenthis --count=5` -> `PREFIX_DOTHAT_THENTHIS_CMD_COUNT`

And follows those rules:
* start with the command prefix (often the same name as the root
  command), passed to `AutoBind()`.
* use the commands and subcommands, then append `CMD` (for `Flags`) or
  `GLOBAL` for `PersistentFlags`.
* the root command doesn't have a command or subcommand and is
  therefore left without a command prefix (becomes `PREFIX_GLOBAL...`
  or `PREFIX_CMD`...)

License
-------

MIT
