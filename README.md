# sbom2csv

sbom2csv is a tool for converting Software Bill of Materials (SBOM) from JSON to CSV format.

## Installation

Describe how to install your tool. If it's available via PyPI, you can simply use:

```shell
pip install sbom2csv
```

## Usage

Here's how you can use sbom2csv:

```shell
sbom2csv -i input.json -f csv -o output.csv
```

## CSV Output Format

The generated CSV file will contain the following columns extracted from the SBOM components:

| Column | Description | Source Field |
|--------|-------------|--------------|
| **Name** | Component name | `name` |
| **Version** | Component version | `version` |
| **Description** | Component description | `description` |
| **Developer** | Component author/developer | `author` |
| **License** | License identifier (SPDX format when available) | `licenses[0].license.id` |
| **User Document** | Link to component website/documentation | `externalReferences` (type: "website") |
| **PURL** | Package URL - standardized identifier | `purl` |

### Example CSV Output

```csv
Name,Version,Description,Developer,License,User Document,PURL
express,4.21.2,"Fast, unopinionated, minimalist web framework",TJ Holowaychuk <tj@vision-media.ca>,MIT,http://expressjs.com/,pkg:npm/express@4.21.2
lodash,4.17.19,Lodash modular utilities.,John-David Dalton <john.david.dalton@gmail.com>,MIT,https://lodash.com/,pkg:npm/lodash@4.17.19
```

### Notes

- The tool processes the `components` array from CycloneDX JSON format SBOMs
- Empty fields will be included as blank values in the CSV
- If multiple licenses exist, only the first license ID is extracted
- The User Document field extracts the first external reference with type "website"


## Contributing

Contributions are welcome! Please read our contributing guidelines for details.

## License

This project is licensed under the Yuan Zhou - see the LICENSE file for details.
