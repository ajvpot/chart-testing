## ct lint

Lint and validate a chart

### Synopsis

Run 'helm lint', version checking, YAML schema validation
on 'Chart.yaml', YAML linting on 'Chart.yaml' and 'values.yaml',
and maintainer validation on

* changed charts (default)
* specific charts (--charts)
* all charts (--all)

in given chart directories.

Charts may have multiple custom values files matching the glob pattern
'*-values.yaml' in a directory named 'ci' in the root of the chart's
directory. The chart is linted for each of these files. If no custom
values file is present, the chart is linted with defaults.

```
ct lint [flags]
```

### Options

```
      --additional-commands strings          Additional commands to run per chart (default: [])
                                             Commands will be executed in the same order as provided in the list and will
                                             be rendered with go template before being executed.
                                             Example: "helm unittest --helm3 -f tests/*.yaml {{ .Path }}"
      --all                                  Process all charts except those explicitly excluded.
                                             Disables changed charts detection and version increment checking
      --chart-dirs strings                   Directories containing Helm charts. May be specified multiple times
                                             or separate values with commas (default [charts])
      --chart-repos strings                  Additional chart repositories for dependency resolutions.
                                             Repositories should be formatted as 'name=url' (ex: local=http://127.0.0.1:8879/charts).
                                             May be specified multiple times or separate values with commas
      --chart-yaml-schema string             The schema for chart.yml validation. If not specified, 'chart_schema.yaml'
                                             is searched in the current directory, '$HOME/.ct', and '/etc/ct', in
                                             that order.
      --charts strings                       Specific charts to test. Disables changed charts detection and
                                             version increment checking. May be specified multiple times
                                             or separate values with commas
      --check-version-increment              Activates a check for chart version increments (default true)
      --config string                        Config file
      --debug                                Print CLI calls of external tools to stdout (caution: setting this may
                                             expose sensitive data when helm-repo-extra-args contains passwords)
      --exclude-deprecated                   Skip charts that are marked as deprecated
      --excluded-charts strings              Charts that should be skipped. May be specified multiple times
                                             or separate values with commas
      --execute-version-increment            Automatically increment the chart version
      --helm-dependency-extra-args strings   Additional arguments for 'helm dependency build' (e.g. ["--skip-refresh"]
      --helm-repo-extra-args strings         Additional arguments for the 'helm repo add' command to be
                                             specified on a per-repo basis with an equals sign as delimiter
                                             (e.g. 'myrepo=--username test --password secret'). May be specified
                                             multiple times or separate values with commas
  -h, --help                                 help for lint
      --lint-conf string                     The config file for YAML linting. If not specified, 'lintconf.yaml'
                                             is searched in the current directory, '$HOME/.ct', and '/etc/ct', in
                                             that order
      --print-config                         Prints the configuration to stderr (caution: setting this may
                                             expose sensitive data when helm-repo-extra-args contains passwords)
      --remote string                        The name of the Git remote used to identify changed charts (default "origin")
      --since string                         The Git reference used to identify changed charts (default "HEAD")
      --target-branch string                 The name of the target branch used to identify changed charts (default "master")
      --validate-chart-schema                Enable schema validation of 'Chart.yaml' using Yamale (default true)
      --validate-maintainers                 Enable validation of maintainer account names in chart.yml.
                                             Works for GitHub, GitLab, and Bitbucket (default true)
      --validate-yaml                        Enable linting of 'Chart.yaml' and values files (default true)
```

### SEE ALSO

* [ct](ct.md)	 - The Helm chart testing tool

