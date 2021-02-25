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

Resulting Output will print automatically from the action.

The results can be later referenced again for use in a separate step if desired using the `results` output from the step

```yaml
- name: reprint results
  run: echo "${{ steps.scan-packaged.outputs.results }}" 
```
