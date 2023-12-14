
### Constraints:

#### NOT NULL:

```postgresql
ALTER TABLE speakers
ALTER COLUMN name SET NOT NULL;


UPDATE speakers
SET organization = 'tbd'
WHERE organization IS NULL;


ALTER TABLE speakers
ALTER COLUMN organization SET NOT NULL;
```

#### Check
```postgresql
ALTER TABLE speakers
ADD CHECK( years_in_role < 100 );
```

#### Unique
```postgresql
--- Alter table to add unique-constraint to email-column
ALTER TABLE speakers
ADD UNIQUE (email);

--- Use unique-constraint to ensure an attendee can only be at one session_timeslot at once
CREATE TABLE registrations (
id integer NOT NULL,
attendee_id integer NOT NULL,
session_timeslot timestamp NOT NULL,
talk_id integer NOT NULL,
UNIQUE (session_timeslot, attendee_id)
);
```

