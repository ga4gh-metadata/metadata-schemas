### Common Attribute Names and Formats

Throughout the schema definitions, a consistent use of common attributes should
be enforced. The following list should serve as guidance for schema developers.

Attribute        | Note
--- | ---
*id*            | the objects ID, used for references at the level of the databas/server instance; locally unique
*name*          | a more descriptive object label/identifier
*description*   | <li>a string describing aspects of the object</li><li>*not* to be used for a list or nested object</li>
*created*       | the time the record was created, in ISO8601 (see below)
*updated*       | the time the record was updated, in ISO8601 (see below)


### Date and Time Format Specifications

* external information: [ISO8601](https://www.w3.org/TR/NOTE-datetime)

Date and time formats are specified as ISO8601 compatible strings, both for
time points as well as for intervals and durations.
An optional required granularity may be specified as part of the respective
attributes' documentations.

#### Units of time

* *Y* = year
* *M* = month
* *D* = day
* *H* = hour
* *M* = minute
* *S* = second
* *.S* = decimal fraction of a second


#### Time points

The specification of a time point is given through the concatenation of

* a date in YYYY-MM-DD
* the designator "T" indicating a following time description
* the time of day in HH:MM:SS.SSS form, where "SSS" represents a decimal
  fraction of a second
* a time zone offset in relation to UTC

**Examples**

* year (YYYY)
    - *2015*
    - Time points with *year* granularity are both common for obfuscated personal data as well as technical metadata (e.g. year of publication of an analysis).

* date (e.g. date of birth) in YYYY-MM-DD
    - *2015-02-10*
    - This represents the standard way of representing a specific day, e.g. a date of birth.

* time stamp in milliseconds in YYYY-MM-DDTHH:MM:SS.SSS
    - *2015-02-10T00:03:42.123Z*
    - Timepoints with millisecond granularity are typical use cases for timing computer generated entries, e.g. the time of a record's update ("updateTime").

**Implementations**

* updated (ubiquitous object time stamp)
* created (ubiquitous object time stamp)


#### Durations

Durations are the most common form of time intervals. They do not refer to
(e.g. start or end) time points.
They are indicated with a leading "P", followed by unit delimited
quantifiers. A leading "T" is required before the start of the time components.
Durations do not have to be normalized; "PT50H" is equally valid as "P2T2H".
A frequent use of durations in biomedical data resources are *age* values,
e.g. "age at diagnosis"; but also "progression free survival", "followup" or "time to recurrence" (these are descriptive labels, which do not necessarily represent GA4GH schema use).

**Examples**

* age in years in PnY
    - *P44Y*
    - This would be the standard annotation for the commonly used age in years, without relation to a date of birth.

* age in years and months in PnYnM
    - *P43Y08M*
    - This represents an age with added months specification.

* short time interval (e.g. 30min in experimental time series) in PTnM
    - *PT30M*
    - A common use for durations is the recording of time points in time series,
      e.g. experimental interventions and observations (collections of cells from
      an in vitro treatment experiment; recurring drug doses in a chemotherapy
      treatment).

#### Time intervals

Time intervals consist of a combination of two time designators. These can be
either two time points for start and end, or one time point and a leading
(time point indicates end) or trailing (time point indicates start) duration.
The time elements are separated by a forward slash "/".

While such anchored time intervals represent an option to capture different time features in a single value and to avoid disconnected references, in the context of the data schema, *anchored intervals* will presumably be used less frequently, with a qualitative anchor ("date of diagnosis", "time of sampling") representing the point of reference.


**Examples**

* age with date of birth in YYYY-MM-DD/PnYnMnD
    - 1967-11-21/P40Y10M05D
    - This value captures both the date of birth (here November 21, 1967)and the age (here 40ys, 10 months and 5 days) at a given time point, e.g. at the date of a medical diagnosis.

* anchored 3 month interval, e.g. a therapy cycle in YYYY-MM-DD/YYYY-MM-DD
    - 2015-04-18/2015-07-17
    - This example demonstrates use of an calendar anchored interval, with given start and end date. A typical example would be the use in medical records, e.g. for a treatment cycle; however, use for data exchange and mining purposes would be less common and usually served with a "duration" (see above).

* experimental intervention of 30min in YYYY-MM-DDTHH:MM/PTnM
    - 2014-12-31T23H45M/PT30M
    - Here is an example for a short term intervention of a 30 minutes duration, e.g. the celebratory exposure to a diluted sample of EtOH with various organic trace compounds, to celebrate the arrival of the new year.
