# Changelog

## 2.9.8
- Fix Ruby 1.9 compatibility in extension installation. PR #531

## 2.9.7
- Fix minutely probes not being loaded from Rails initializers. PR #528

## 2.9.6
- Print link to diagnose docs on unsuccessful demo command. PR #512
- Add support for minutely probe `.dependencies_present?` check. PR #523
- Do not activate Sidekiq minutely probe on unsupported Redis gem versions.
  PR #523.

## 2.9.5
- Improve logging in minutely probes. PR #508
- Delay the first minutely probe for a bit, since it might take some
  time for dependencies to initialize. PR #511

## 2.9.4
- Log error backtraces in minutely probes as debug messages. PR #495
- Don't add cluster behavior in Puma single mode. PR #504
- Only register ActionView event formatter in Rails. PR #503
- Convert Sidekiq latency from seconds to ms. PR #505

## 2.9.3
- Remove GCProbe. PR #501

## 2.9.2
- Fix Puma.stats calls. PR #496
- Only send Puma metrics if available. PR #497
- Track memory metrics of the current process. PR #499

## 2.9.1
- Fix memory leak in custom metrics key names.
  Commit 9064e2ccfd19ee05c333d0ecda4deafdd743629e

## 2.9.0
- Fix installations using git source. PR #455
- Track installation results in installation report. PR #450
- Fix Rails 6 deprecation warnings. PR #460, PR #478, PR #483
- Improve error handling in minutely probes mechanism. PR #467
- Only allow one minutely probe thread to run at a time. PR #469
- Change minutely probes register method to use a key for every probe. PR #473
- Send Sidekiq metrics by default. PR #471
- Send MongoDB metrics by default. PR #472
- Fix Ruby 2.6 deprecation warnings. PR #479
- Support blocks for `Appsignal.send_error` to add more metadata to the
  AppSignal transaction. PR #481
- Move instrumentation & metrics helpers to modules. PR #487
- Add Puma minutely probe. PR #488
- Log invalid EventFormatter registrations as errors. PR #491
- Support container CPU host metrics.
  Commit f2fca1ec5a850cd84fbc8cefe63af8f039ebb155
- Support StatsD server in agent.
  Commit f2fca1ec5a850cd84fbc8cefe63af8f039ebb155
- Fix samples being reported for multiple namespaces.
  Commit f2fca1ec5a850cd84fbc8cefe63af8f039ebb155
- Report memory and swap usage in percent using the memory_usage and
  swap_usage metrics. Commit f2fca1ec5a850cd84fbc8cefe63af8f039ebb155

## 2.8.4
- Log memory usage of agent if high.
  Commit 46cf3770e13eff9f5fccbf8a4525a8dbfd8eeaad
- Fix `Appsignal::Transaction.pause!`. PR #482

## 2.8.3
- Fix multi user permission issue for agent directories and files.
  Commit ab1b35f850777d5999b41627d75be0b3904bc0a1

## 2.8.2
- Remove Bundler requirement from diagnose command. PR #451
- Fix Delayed::Job action name reporting for structs. PR #463

## 2.8.1
- Fix installation on Ruby 2.6 for libc and musl library builds. PR #453

## 2.8.0
- Group extension and agent tests in diagnose output. PR #437
- Add diagnose --[no-]send-report option. PR #438
- Print deprecation warnings to STDOUT as well. PR #439
- Diagnose command starts the AppSignal logger. PR #440
- Send appsignal.log file contents with diagnose report. PR #442
- Track source of config option for diagnose report. PR #444
- Link back to AppSignal diagnose report page. Claim you reports. PR #445
- Print only last 10 lines of files in diagnose report output. PR #442 & #447
- Support container memory host metrics better. PR #448
- Build dynamic musl extension library. Supports JRuby for musl builds. PR #448
- Change `files_world_accessible` permissions to not make files executable.
  PR #448
- Make agent debug logging for disk IO metrics more robust. PR #448

## 2.7.3 Beta
- Add user and group context to diagnose report. PR #436
- Add user and group context to agent logs. PR #436
- Fixes for running with multiple users

## 2.7.2
- Change the order of instructions in the install script for Rails. PR #433
- Fix linking issues on multi-stage build setups. PR #434

## 2.7.1
- Improve error log on unsupported architecture and build combination on
  install. PR #426
- Improve performance when garbage collection profiling is disabled. PR #429

## 2.7.0
- Detect Kubernetes containers as containers for `running_in_container`
  config option. Commit 60822aac24ccc394df073091c64f05096455942d.
- Fix in memory logger initialization. PR #416
- Organize classes in their own files. PR #417
- Move tag value limit handling to extension. PR #418
- Add working_directory_path config option. PR #421
- Use doubles values in custom metrics functions. PR #422
- Bump agent to e41c3c0. Commit 8056af037f82eda156c5946911012e5c742b5664

## 2.6.1
- Remove request_headers warning and use sane default. PR #410
- Fix metrics format for internal agent metrics. PR #411

## 2.6.0
- Enable frozen strings by default. PR #384
- Add `revision` config option. PR #388
- Avoid generating unique action names for Padrino. PR #393
- Add `request_headers` filter configuration. PR #395
- Support tags for custom metrics. PR #398
- Add filter_session_data config option. PR #402 & #409
- Move default hostname behavior to extension. PR #404
- Add `request_headers` config to installation step. PR #406
- Rename ParamsSanitizer to HashSanitizer. PR #408
- Fix empty action name issue. Commit b292c2c93c8935ab54fc4d16598fa534c9cc9c90

## 2.5.3
- Fix Sidekiq action names containing arguments. PR #401

## 2.5.2
- Support Sidekiq delay extension for ActiveRecord instances. If using this
  feature in your app, an update is strongly recommended! PR #387
- Improve custom event formatter registration. An event formatter can now be
  registered in a Rails initializer after AppSignal has been loaded/started.
  PR #397

## 2.5.1
- Improve internal sample storage in agent.
  Commit 2c8eae26685c7a1517cf2e57b44edd1557a502f2
- No longer set _APPSIGNAL_AGENT_VERSION environment variable. PR #385

## 2.5.0
- Fix Capistrano config overrides. PR #375
- Add JRuby beta support. PR #376
- Fix locking issue on diagnose mode run.
  Commit e6c6de811f8115a73050fc865e89dd4945ddec57
- Increase stored length of error messages.
  Commit e6c6de811f8115a73050fc865e89dd4945ddec57

## 2.4.3
- Store more details for Redis events. PR #374

## 2.4.2
- Store agent architecture rather than platform. PR #367
- Improve documentation for `Appsignal.monitor_transaction` better.
  Commit e53987ba36a79fc8883f2e59322946297ddee773
- Change log level from info to debug for value comparing failures.
  Commit ecef28b28edaff46b95f53a916c93021dc763160
- Collect free memory host metric.
  Commit ecef28b28edaff46b95f53a916c93021dc763160
- Fix crashes when Set wasn't required before AppSignal, such as in the CLI.
  PR #373

## 2.4.1
- Add Que integration. PR #361
- Support Sidekiq delayed extension job action names better. Now action names
  are reported as their class and class method name (`MyClass.method`), rather
  than `Sidekiq::Extensions::DelayedClass#perform` for all jobs through that
  extension. PR #362
- Support Sidekiq Enterprise encrypted values. PR #365
- Use musl build for older libc systems. PR #366

## 2.4.0
- Add separate GNU linux build. PR #351 and
  Commit d1763f4dcb685608468a73f3192226f60f66b217
- Add separate FreeBSD build
  Commit d1763f4dcb685608468a73f3192226f60f66b217
- Fix crashes when using a transaction from multiple processes in an
  unsupported way.
  Commit d1763f4dcb685608468a73f3192226f60f66b217
- Auto restart agent when none is running
  Commit d1763f4dcb685608468a73f3192226f60f66b217
- Add `appsignal_user` Capistrano config option. PR #355
- Track Exception-level exceptions. PR #356
- Add tags and namespace arguments to `Appsignal.listen_for_error`. PR #357
- Revert Sidekiq delayed extension job action names fix.
  Commit 9b84a098604de5ef5e52645ba7fcb09d84f66eaa

## 2.3.7
- Support Sidekiq delayed extension job action names better. Now action names
  are reported as their class and class method name (`MyClass.method`), rather
  than `Sidekiq::Extensions::DelayedClass#perform` for all jobs through that
  extension. PR #348

## 2.3.6
- Allow configuration of permissions of working directory. PR #336
- Fix locking bug that delayed extension shutdown.
  Commit 51d90bb1207affc2c88f7cff5035a2c36acf9784
- Log extension start with app revision if present
  Commit 51d90bb1207affc2c88f7cff5035a2c36acf9784

## 2.3.5

Yanked

## 2.3.4
- Fix naming for ActiveJob integration with DelayedJob. PR #345

## 2.3.3
- Accept mixed case env variable values for the `true` value. PR #333
- Don't record sensitive HTTP_X_AUTH_TOKEN header. PR #334
- Support dry run option for Capistrano 3.5.0 and higher. PR #339
- Agent and extension update. Improve agent connection handling. Commit
  e75d2f9b520d46f6cd0266b484b2c26c3bdc8882

## 2.3.2
- Improve Rake argument handling. Allow for more detailed view of which
  arguments a tasks receives. PR #328

## 2.3.1
- Fix ActiveSupport::Notifications hook not supporting non-string names for
  events. PR #324

## 2.3.0
- Fix Shoryuken instrumentation when body is a string. PR #266
- Enable ActiveSupport instrumentation at all times. PR #274
- Add parameter filtering for background jobs. Automatically uses the AppSignal
  parameter filtering. PR #280
- Improve log messages for transactions. PR #293
- Remove thread_safe dependency. PR #294
- Add `Transaction#params` attribute for custom parameters. PR #295
- Fix queue time on DelayedJob integration. PR #297
- Add ActionCable support. PR #309
- Finish ActiveSupport notifications events when they would encounter a `raise`
  or a `throw`. PR #310
- Add `ignore_namespaces` option. PR #312
- Truncate lengthy parameter values to 2000 characters.
  Commit 65de1382f5f453b624781cde6e0544c89fdf89ef and
  d3ca2a545fb22949f3369692dd57d49b4936c739.
- Disable gracefully on Microsoft Windows. PR #313
- Add tags and namespace arguments to `Appsignal.set_error`. PR #317

## 2.2.1
- Fix support for Rails 5.1. PR #286
- Fix instrumentation that would report a duration of `0ms` for all DataMapper
  queries. PR #290
- Finish events when `Appsignal.instrument` encounters a `raise` or a `throw`.
  PR #292

## 2.2.0
- Support Ruby 2.4 better. PR #234
- Initial setup for documenting the Ruby gem's code. PR #243
- Move `running_in_container` auto detection to extension for easy reuse.
  PR #249
- Allow overriding of action and namespace for a transaction. PR #254
- Prefix all agent configuration environment variables with an underscore to
  separate the two usages. PR #258
- Force agent to run in diagnostic mode even when the user config is set to
  `active: false`. PR #260
- Stub JS error catching endpoint when not active. PR #263
- Use better event names for Padrino integration. PR #265
- No longer gzip payloads send by the Ruby gem transmitter. PR #269
- Send diagnostics data report to AppSignal on request. PR #270
- When JS exception endpoint payload is empty return 400 code. PR #271
- Remove hardcoded DNS servers from agent and add config option. PR #278

## 2.1.2
- Fix error with Grape request methods defined with symbols. PR #259

## 2.1.1
- Fix DNS issue related to the musl build.
  Commit 732c877de8faceabe8a977bf80a82a6a89065c4d and
  84e521d20d4438f7b1dda82d5e9f1f533ae27c4b
- Update benchmark and add load test. PR #248
- Fix configuring instrument Redis and Sequel from env. PR #257

## 2.1.0
- Add support for musl based libc (Alpine Linux). PR #229
- Implement `Appsignal.is_ignored_error?` and `Appsignal.is_ignored_action?`
  logic in the AppSignal extension. PR #224
- Deprecate `Appsignal.is_ignored_error?`. PR #224
- Deprecate `Appsignal.is_ignored_action?`. PR #224
- Enforce a coding styleguide with RuboCop. PR #226
- Remove unused `Appsignal.agent` attribute. PR #244
- Deprecate unused `Appsignal::AuthCheck` logger argument. PR #245

## 2.0.6
- Fix `Appsignal::Transaction#record_event` method call. PR #240

## 2.0.5
- Improved logging for agent connection issues.
  Commit cdf9d3286d704e22473eb901c839cab4fab45a6f
- Handle nil request/environments in transactions. PR #231

## 2.0.4
- Use consistent log format for both file and STDOUT logs. PR #203
- Fix log path in `appsignal diagnose` for Rails applications. PR #218, #222
- Change default log path to `./log` rather than project root for all non-Rails
  applications. PR #222
- Load the `APPSIGNAL_APP_ENV` environment configuration option consistently
  for all integrations. PR #204
- Support the `--environment` option on the `appsignal diagnose` command. PR
  #214
- Use the real system `/tmp` directory, not a symlink. PR #219
- Run the AppSignal agent in diagnose mode in the `appsignal diagnose` command.
  PR #221
- Test for directory and file ownership and permissions in the
  `appsignal diagnose` command. PR #216
- Test if current user is `root` in the `appsignal diagnose` command. PR #215
- Output last couple of lines from `appsignal.log` on agent connection
  failures.
- Agent will no longer fail to start if no writable log path is found.
  Commit 8920865f6158229a46ed4bd1cc98d99a849884c0, change in agent.
- Internal refactoring of the test suite and the `appsignal install` command.
  PR #200, #205

## 2.0.3
- Fix JavaScript exception catcher throwing an error on finishing a
  transaction. PR #210

## 2.0.2
- Fix Sequel instrumentation overriding existing logic from extensions. PR #209

## 2.0.1
- Fix configuration load order regression for the `APPSIGNAL_PUSH_API_KEY`
  environment variable's activation behavior. PR #208

## 2.0.0
- Add `Appsignal.instrument_sql` convenience methods. PR #136
- Use `Appsignal.instrument` internally instead of ActiveSupport
  instrumentation. PR #142
- Override ActiveSupport instrument instead of subscribing. PR #150
- Remove required dependency on ActiveSupport. Recommended you use
  `Appsignal.instrument` if you don't need `ActiveSupport`. PR #150 #142
- Use have_library to link the AppSignal extension `libappsignal`. PR #148
- Rename `appsignal_extension.h` to `appsignal.h`.
  Commit 9ed7c8d83f622d5a79c5c21d352b3360fd7e8113
- Refactor rescuing of Exception. PR #173
- Use GC::Profiler to track garbage collection time. PR #134
- Detect if AppSignal is running in a container or Heroku. PR #177 #178
- Change configuration load order to load environment settings after
  `appsignal.yml`. PR #178
- Speed up payload generation by letting the extension handle it. PR #175
- Improve `appsignal diagnose` formatting and output more data. PR #187
- Remove outdated `appsignal:diagnose` rake tasks. Use `appsignal diagnose`
  instead. PR #193
- Fix JavaScript exception without names resulting in errors themselves. PR #188
- Support namespaces in Grape routes. PR #189
- Change STDOUT output to always mention "AppSignal", not "Appsignal". PR #192
- `appsignal notify_of_deploy` refactor. `--name` will override any
  other `name` config. `--environment` is only required if it's not set in the
  environment. PR #194
- Allow logging to STDOUT. Available for the Ruby gem and C extension. The
  `appsignal-agent` process will continue log to file. PR #190
- Remove deprecated methods. PR #191
- Send "ruby" implementation name with version number for better identifying
  different language implementations. PR #198
- Send demonstration samples to AppSignal using the `appsignal install`
  command instead of asking the user to start their app. PR #196
- Add `appsignal demo` command to test the AppSignal demonstration samples
  instrumentation manually and not just during the installation. PR #199

## 1.3.6
- Support blocks arguments on method instrumentation. PR #163
- Support `APPSIGNAL_APP_ENV` for Sinatra. PR #164
- Remove Sinatra install step from "appsignal install". PR #165
- Install Capistrano integration in `Capfile` instead of `deploy.rb`. #166
- More robust handing of non-writable log files. PR #160 #158
- Cleaner internal exception handling. PR #169 #170 #171 #172 #173
- Support for mixed case keywords in sql lexing. appsignal/sql_lexer#8
- Support for inserting multiple rows in sql lexing. appsignal/sql_lexer#9
- Add session_overview to JS transaction data.
  Commit af2d365bc124c01d7e9363e8d825404027835765

## 1.3.5

- Fix SSL certificate config in appsignal-agent. PR #151
- Remove mounted_at Sinatra middleware option. Now detected by default. PR #146
- Sinatra applications with middleware loading before AppSignal's middleware
  would crash a request. Fixed in PR #156

## 1.3.4

- Fix argument order for `record_event` in the AppSignal extension

## 1.3.3

- Output AppSignal environment on `appsignal diagnose`
- Prevent transaction crashes on Sinatra routes with optional parameters
- Listen to `stage` option to Capistrano 2 for automatic environment detection
- Add `appsignal_env` option to Capistrano 2 to set a custom environment

## 1.3.2
- Add method to discard a transaction
- Run spec suite with warnings, fixes for warnings

## 1.3.1
- Bugfix for problem when requiring config from installer

## 1.3.0
- Host metrics is now enabled by default
- Beta of minutely probes including GC metrics
- Refactor of param sanitization
- Param filtering for non-Rails frameworks
- Support for modular Sinatra applications
- Add Sinatra middleware to `Sinatra::Base` by default
- Allow a new transaction to be forced by sinatra instrumentation
- Allow hostname to be set with environment variable
- Helpers for easy method instrumentation
- `Appsignal.instrument` helper to easily instrument blocks of code
- `record_event` method to instrument events without a start hook
- `send_params` is now configurable via the environment
- Add DataMapper integration
- Add webmachine integration
- Allow overriding Padrino environment with APPSIGNAL_APP_ENV
- Add mkmf.log to diagnose command
- Allow for local install with bundler `bundle exec rake install`
- Listen to `stage` option to Capistrano 3 for automatic environment detection
- Add `appsignal_env` option to Capistrano 3 to set a custom environment

## 1.2.5
- Bugfix in CPU utilization calculation for host metrics

## 1.2.4
- Support for adding a namespace when mounting Sinatra apps in Rails
- Support for negative numbers and ILIKE in the sql lexer

## 1.2.3
- Catch nil config for installer and diag
- Minor performance improvements
- Support for arrays, literal value types and function arguments in sql lexer

## 1.2.2
- Handle out of range numbers in queue lenght and metrics api

## 1.2.1
- Use Dir.pwd in CLI install wizard
- Support bignums when setting queue length
- Support for Sequel 4.35
- Add env option to skip errors in Sinatra
- Fix for queue time calculation in Sidekiq (by lucasmazza)

## 1.2.0
- Restart background thread when FD's are closed
- Beta version of collecting host metrics (disabled by default)
- Hooks for Shuryoken
- Don't add errors from env if raise_errors is off for Sinatra

## 1.1.9
- Fix for race condition when creating working dir exactly at the same time
- Make diag Rake task resilient to missing config

## 1.1.8
- Require json to fix problem with using from Capistrano

## 1.1.7
- Make logging resilient for closing FD's (daemons gem does this)
- Add support for using Resque through ActiveJob
- Rescue more expections in json generation

## 1.1.6
- Generic Rack instrumentation middleware
- Event formatter for Faraday
- Rescue and log errors in transaction complete and fetching params

## 1.1.5
- Support for null in sql sanitization
- Add require to deploy.rb if present on installation
- Warn when overwriting already existing transaction
- Support for x86-linux
- Some improvements in debug logging
- Check of log file path is writable
- Use bundled CA certs when installing agent

## 1.1.4
- Better debug logging for agent issues
- Fix for exception with nil messages
- Fix for using structs as job params in Delayed Job

## 1.1.3
- Fix for issue where Appsignal.send_exception clears the current
  transaction if it is present
- Rails 3.0 compatibility fix

## 1.1.2
- Bug fix in notify of deploy cli
- Better support for nil, true and false in sanitization

## 1.1.1
- Collect global metrics for GC durations (in beta, disabled by default)
- Collect params from Delayed Job in a reliable way
- Collect perams for Delayed Job and Sidekiq when using ActiveJob
- Official Grape support
- Easier installation using `bundle exec appsignal install`

## 1.1.0
Yanked

## 1.0.7
- Another multibyte bugfix in sql sanizitation

## 1.0.6
- Bugfix in sql sanitization when using multibyte utf-8 characters

## 1.0.5
- Improved sql sanitization
- Improved mongoid/mongodb sanitization
- Minor performance improvements
- Better handling for non-utf8 convertable strings
- Make gem installable (but not functional) on JRuby

## 1.0.4
- Make working dir configurable using `APPSIGNAL_WORKING_DIR_PATH` or `:working_dir_path`

## 1.0.3
- Fix bug in completing JS transactions
- Make Resque integration robust for bigger payloads
- Message in logs if agent logging cannot initialize
- Call `to_s` on DJ id to see the id when using MongoDB

## 1.0.2
- Bug fix in format of process memory measurements
- Event formatter for `instantiation.active_record`
- Rake integration file for backwards compatibility
- Don't instrument mongo-ruby-driver when transaction is not present
- Accept method calls on extension if it's not loaded
- Fix for duplicate notifications subscriptions when forking

## 1.0.1
- Fix for bug in gem initialization when using `safe_yaml` gem

## 1.0.0
- New version of event formatting and collection
- Use native library and agent
- Use API V2
- Support for Mongoid 5
- Integration into other gems with a hooks system
- Lots of minor bug fixes and improvements

## 0.11.15
- Improve Sinatra support

## 0.11.14
- Support ActiveJob wrapped jobs
- Improve proxy support
- Improve rake support

## 0.11.13
- Add Padrino support
- Add Rake task monitoring
- Add http proxy support
- Configure Net::HTTP to only use TLS
- Don't send queue if there is no content
- Don't retry transmission when response code is 400 (no content)
- Don't start Resque IPC server when AppSignal is not active
- Display warning message when attempting to send a non-exception to `send_exception`
- Fix capistrano 2 detection
- Fix issue with Sinatra integration attempting to attach an exception to a transaction that doesn't exist.

## 0.11.12
- Sanitizer will no longer inspect unknown objects, since implementations of inspect sometimes trigger unexpected behavior.

## 0.11.11
- Reliably get errors in production for Sinatra

## 0.11.10
- Fix for binding bug in exceptions in Resque
- Handle invalidly encoded characters in payload

## 0.11.9
- Fix for infinite attempts to transmit if there is no valid api key

## 0.11.8
- Add frontend error catcher
- Add background job metadata (queue, priority etc.) to transaction overview
- Add APPSIGNAL_APP_ENV variable to Rails config, so you can override the environment
- Handle http queue times in microseconds too

## 0.11.7
- Add option to override Job name in Delayed Job

## 0.11.6
- Use `APPSIGNAL_APP_NAME` and `APPSIGNAL_ACTIVE` env vars in config
- Better Sinatra support: Use route as action and set session data for Sinatra

## 0.11.5
- Add Sequel gem support (https://github.com/jeremyevans/sequel)

## 0.11.4
- Make `without_instrumentation` thread safe

## 0.11.3
- Support Ruby 1.9 and up instead of 1.9.3 and up

## 0.11.2
- If APP_REVISION environment variable is set, send it with the log entry.

## 0.11.1
- Allow a custom request_class and params_method on  Rack instrumentation
- Loop through env methods instead of env
- Add HTTP_CLIENT_IP to env methods

## 0.11.0
- Improved inter process communication
- Retry sending data when the push api is not reachable
- Our own event handling to allow for more flexibility and reliability
  when using a threaded environment
- Resque officially supported!

## 0.10.6
- Add config option to skip session data

## 0.10.5
- Don't shutdown in `at_exit`
- Debug log about missing name in config

## 0.10.4
- Add REQUEST_URI and PATH_INFO to env params allowlist

## 0.10.3
- Shut down all operations when agent is not active
- Separately rescue OpenSSL::SSL::SSLError

## 0.10.2
- Bugfix in event payload sanitization

## 0.10.1
- Bugfix in event payload sanitization

## 0.10.0
- Remove ActiveSupport dependency
- Use vendored notifications if ActiveSupport is not present
- Update bundled CA certificates
- Fix issue where backtrace can be nil
- Use Appsignal.monitor_transaction to instrument and log errors for
  custom actions
- Add option to ignore a specific action

## 0.9.6
- Convert to primitives before sending through pipe

## 0.9.5
Yanked

## 0.9.4
- Log Rails and Sinatra version
- Resubscribe to notifications after fork

## 0.9.3
- Log if appsignal is not active for an environment

## 0.9.2
- Log Ruby version and platform on startup
- Log reason of shutting down agent

## 0.9.1
- Some debug logging tweaks

## 0.9.0
- Add option to override Capistrano revision
- Expanded deploy message in Capistrano
- Refactor of usage of Thread.local
- Net::HTTP instrumentation
- Capistrano 3 support

## 0.8.15
- Exception logging in agent thread

## 0.8.14
- Few tweaks in logging
- Clarify Appsignal::Transaction.complete! code

## 0.8.13
- Random sleep time before first transmission of queue

## 0.8.12
- Workaround for frozen string in Notification events
- Require ActiveSupport::Notifications to be sure it's available

## 0.8.11
- Skip enqueue, send_exception and add_exception if not active

## 0.8.10
- Bugfix: Don't pause agent when it's not active

## 0.8.9
Yanked

## 0.8.8
- Explicitely require securerandom

## 0.8.7
- Dup process action event to avoid threading issue
- Rescue failing inspects in param sanitizer
- Add option to pause instrumentation

## 0.8.6
- Resque support (beta)
- Support tags in Appsignal.send_exception
- Alias tag_request to tag_job, for background jobs
- Skip sanitization of env if env is nil
- Small bugfix in forking logic
- Don't send params if send_params is off in config
- Remove --repository option in CLI
- Name option in appsignal notify_of_deploy CLI
- Don't call to_hash on ENV
- Get error message in CLI when config is not active

## 0.8.5
- Don't require revision in CLI notify_of_deploy

## 0.8.4
- Skip session sanitize if not a http request
- Use appsignal_config in Capistrano as initial config

## 0.8.3
- Restart thread when we've been forked
- Only notify of deploy when active in capistrano
- Make sure env is a string in config

## 0.8.2
- Bugfix in Delayed Job integration
- appsignal prefix when logging to stdout
- Log to stdout on Shelly Cloud

## 0.8.1
- Fix in monitoring of queue times

## 0.8.0
- Support for background processors (Delayed Job and Sidekiq)

## 0.7.1
- Better support for forking webservers

## 0.7.0
- Mayor refactor and cleanup
- New easier onboarding process
- Support for Rack apps, including experimental Sinatra integration
- Monitor HTTP queue times
- Always log to stdout on Heroku

## 0.6.7
- Send HTTP_X_FORWARDED_FOR env var

## 0.6.6
- Add Appsignal.add_exception

## 0.6.5
- Fix bug where fast requests are tracked with wrong action

## 0.6.4
- More comprehensive debug logging

## 0.6.3
- Use a mutex around access to the aggregator
- Bugfix for accessing connection config in Rails 3.0
- Add Appsignal.tag_request
- Only warn if there are duplicate push keys

## 0.6.2
- Bugfix in backtrace cleaner usage for Rails 4

## 0.6.1
- Bugfix in Capistrano integration

## 0.6.0
- Support for Rails 4
- Data that's posted to AppSignal is now gzipped
- Add Appsignal.send_exception and Appsignal.listen_for_exception
- We now us the Rails backtrace cleaner

## 0.5.5
- Fix minor bug

## 0.5.4
- Debug option in config to get detailed logging

## 0.5.3
- Fix minor bug

## 0.5.2
- General improvements to the Rails generator
- Log to STDOUT if writing to log/appsignal.log is not possible (Heroku)
- Handle the last transactions before the rails process shuts down
- Require 'erb' to enable dynamic config
