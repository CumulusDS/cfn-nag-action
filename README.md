[![Create Release](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/release.yml/badge.svg)](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/release.yml)  

[![Import Labels](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/labels_import.yml/badge.svg)](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/labels_import.yml)  [![Sync Labels](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/labels_sync.yml/badge.svg)](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/labels_sync.yml)  

[![PR AutoLabeler](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/autolabeler.yml/badge.svg)](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/autolabeler.yml)  [![Assigner](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/assign.yml/badge.svg)](https://github.com/CumulusDS/cfn-nag-action/actions/workflows/assign.yml)  

Runs cfn-nag-scan with scan results as output

### Inputs
#### `version`
Used to specify a specific desired version of cfn-nag-scan.  
Non-required input.  
Defaults to the latest available version if left blank.

#### `path`
Desired path to scan.  
Non-required input.  
Defaults to current directory.

#### `args`
Additional cli arguments to pass in to cfn_nag_scan.  
Non-required input.  
Defaults to `--print-suppression`

### Outputs
#### `results`
Results of the scan

### Example usage
```yaml
      - name: cfn_nag_scan packaged template
        id: scan-packaged
        uses: CumulusDS/cfn-nag-action@v0.0.1
        with:
          path: .serverless/*.json
```

The results can be later referenced again for use in a separate step if desired using the `results` output from the step.  
In order to reference the `result` output, you must assign and `id` to the step for future referencing.

```yaml
      - name: reprint results
        run: echo "${{ steps.scan-packaged.outputs.results }}" 
```
