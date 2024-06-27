# Timestamps Extension Specification

- **Title:** Timestamps
- **Identifier:** <https://fiboa.github.io/timestamps-extension/v0.1.0/schema.yaml>
- **Property Name Prefix:** datetime
- **Extension Maturity Classification:** Proposal
- **Owner**: @m-mohr @cholmes

This document explains the Timestamps Extension to the
[Field Boundaries for Agriculture (fiboa) Specification](https://github.com/fiboa/specification).

Timestamps for the lifetime of a field boundary in the categories:
- Seasonal Activity
- Determination
- Derivatives
- Administrative
- Data Management

---

- Examples:
  - [GeoJSON](examples/geojson/)
  - [GeoParquet](examples/geoparquet/)
- [Schema](schema/schema.yaml)
- [Changelog](./CHANGELOG.md)

## Properties

The properties in the tables below can be used in these parts of fiboa documents:

- [ ] Collection
- [x] Feature Properties

All properties must be provided in UTC!

### Seasonal Activity

| Property Name          | Type     | Description                   |
| ---------------------- | -------- | ----------------------------- |
| datetime:season_start  | datetime | Start of the season           |
| datetime:tillage       | datetime | Seasonal: Tillage             |
| datetime:first_harvest | datetime | Seasonal: First harvest       |
| datetime:last_harvest  | datetime | Seasonal: Last harvest        |
| datetime:season_end    | datetime | End of the season             |

### Determination

| Property Name                | Type     | Description                                                  |
| ---------------------------- | -------- | ------------------------------------------------------------ |
| datetime:first_determination | datetime | The first time at which the field did exist and was observed |
| *determination_datetime*     | datetime | *From fiboa core for completeness* - The last time at which the field did exist and was observed |

The extensions assumes that the provided determination timestamps are homogenously captured,
i.e. `determination_method` applies to all activity-related timestamps above.

### Derivatives

Datetimes related to field boundaries that were derived from other sources,
e.g. through machine learning from satellite imagery.

| Property Name            | Type     | Description                                                  |
| ------------------------ | -------- | ------------------------------------------------------------ |
| datetime:processed       | datetime | Algorithm runtime                                            |
| *determination_datetime* | datetime | *From fiboa core for completeness* - Time the source data was measured |

### Administrative

| Property Name       | Type     | Description                                |
| ------------------- | -------- | ------------------------------------------ |
| datetime:planned    | datetime | Planning started                           |
| datetime:introduced | datetime | Field was physically layed out             |
| datetime:ceased     | datetime | Field is physically not present any longer |

### Data Management

| Property Name        | Type     | Description                                                  |
| -------------------- | -------- | ------------------------------------------------------------ |
| datetime:created     | datetime | Field boundary was added to dataset                          |
| datetime:updated     | datetime | Field boundary was last modified in the dataset              |
| datetime:valid_from  | datetime | Field boundary in dataset is valid from                      |
| datetime:valid_until | datetime | Field boundary in dataset is valid until / expires           |
| datetime:deleted     | datetime | Field boundary has will be (or has been) deleted from the dataset |

## Contributing

See the [contributing guideline](CONTRIBUTING.md) for more details.
