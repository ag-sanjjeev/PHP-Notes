## &#10162; Date and Time:
PHP provides a robust set of functions and classes to handle date and time related operations.

### &#9780; Overview:
1. [Date Functions](#-date-functions)
2. [Time Functions](#-time-functions)
3. [DateTime Class](#-datetime-class)
4. [DateTimeImmutable Class](#-datetimeimmutable-class)
5. [DateInterval Class](#-dateinterval-class)
6. [DatePeriod Class](#-dateperiod-class)
7. [Formatting Dates and Times](#-formatting-dates-and-times)
8. [Parsing Relative Dates and Times](#-parsing-relative-dates-and-times)
9. [Date and Time Constants](#-date-and-time-constants)
10. [Timezones](#-timezones)
11. [Key Points](#-key-points)

### &#10022; Date Functions:
- `date()` function:
It formats a local date and time.

*Syntax:* 

`date(format, timestamp)`

*Example:*
```php
$date = date("Y-m-d H:i:s");
echo $date; // Output: 2024-11-22 12:53:00 (example)
```

- `getdate()` function:

The `getdate()` function returns an associative array of details like the year, month, day, hour, minute, second, weekday, and more for given timestamp.

*Syntax:*

- It accepts optional `timestamp` integer of Unix timestamp. If omitted, the current time is used.
```php
getdate(timestamp);
```

*Example:*
```php
$timestamp = time();
$date_array = getdate($timestamp);

echo "Year: " . $date_array['year'] . nl2br("\n");
echo "Month: " . $date_array['mon'] . nl2br("\n");
echo "Day: " . $date_array['mday'] . nl2br("\n");
echo "Hour: " . $date_array['hours'] . nl2br("\n");
echo "Minute: " . $date_array['minutes'] . nl2br("\n");
echo "Second: " . $date_array['seconds'] . nl2br("\n");
echo "Weekday: " . $date_array['weekday'] . nl2br("\n");
echo "Month Name: " . $date_array['month'] . nl2br("\n");
```

- `checkdate()` function:

It validates a given date.
  
*Syntax:* 

`checkdate(month, day, year)`

*Example:*
```php
if (checkdate(11, 22, 2024)) {
    echo "November 22, 2024 is a valid date.";
}
```

- `idate()` function:

The `idate()` function is used to get specific parts of a date or time. It is useful for extracting individual components like the day, month, year, hour, minute, and second.

*Syntax:*

- `format`: It accepts a single-character format specifier.
- `timestamp`: It accepts second and optional Unix timestamp. If omitted, the current time is used.
```php
idate(format, timestamp);
```

*Example:*
```php
$year = idate('Y');
$month = idate('m');
$day = idate('d');

echo "Today is: " . $day . "/" . $month . "/" . $year;
```

- `gmdate()` function:

The `gmdate()` function is used to format a GMT/UTC date and time. It is similar to the `date()` function, but it always returns the time in GMT.

*Syntax:*

- `format`: It accepts a format specifier. It uses the same format specifiers as the `date()` function.
- `timestamp`: It accepts second and an optional integer Unix timestamp. If omitted, the current time is used.
```php
gmdate(format, timestamp);
```

*Example:*
```php
$gmt_date_time = gmdate("Y-m-d H:i:s");
echo $gmt_date_time; // Output: 2024-11-22 09:56:58 (GMT) (example)
```

- `getlastmod()` function:

The `getlastmod()` function is used to retrieve the last modification time of the current script. It returns a Unix timestamp and represents the elapsed seconds since the Unix epoch (January 1, 1970 00:00:00 GMT).

*Syntax:*
```php
int getlastmod(void)
```

*Example:*
```php
$last_modified = getlastmod();
// Format date and time
$formatted_date = date("F d, Y H:i:s", $last_modified);
echo "Last modified: " . $formatted_date; // Output: Last modified: November 22, 2024 15:29:55 (example)
```

### &#10022; Time Functions:
- `time() function`:

It returns the current Unix timestamp (seconds since the Unix epoch).
  
*Example:*
```php
$timestamp = time();
echo $timestamp; // Output: 1732260432 (example)
```

- `mktime()`:

It creates a Unix timestamp from specified date and time parameters.

*Syntax:* 

`mktime(hour, minute, second, month, day, year)`

*Example:*
```php
$timestamp = mktime(12, 53, 00, 11, 22, 2024);
echo date("Y-m-d H:i:s", $timestamp); // Output: 2024-11-22 12:53:00 (example)
```

- `gmmktime()` function:

The `gmmktime()` function is used to get the Unix timestamp for a given GMT date. It is similar to `mktime()` function, but it always returns a GMT timestamp.

*Syntax:*
```php
int gmmktime(int $hour, int $minute, int $second, int $month, int $day, int $year, int $is_dst = -1);
```

*Example:*
```php
$timestamp = gmmktime(12, 30, 0, 11, 22, 2023);
echo $timestamp; // Output: 1700656200 (Unix timestamp)

// Format date and time:
$formatted_date = date('Y-m-d H:i:s', $timestamp);
echo $formatted_date; // Output: 2023-11-22 18:00:00
```

- `filemtime()` function:

The `filemtime()` function is used to retrieve the last modified time of a specified file. It returns a Unix timestamp and represents the elapsed seconds since the Unix epoch (January 1, 1970 00:00:00 GMT).

*Syntax:*

- `filename`: The path to the file.
```php
int filemtime(string $filename)
```

*Example:*
```php
$filename = "article1.php";
$lastModified = filemtime($filename);
// Format date and time
$formattedDate = date("F d, Y H:i:s", $lastModified);
echo "Last modified: " . $formattedDate; // Output: Last modified: November 22, 2024 15:29:55 (example)
```

### &#10022; DateTime Class:
It represents a specific date and time. And it provides methods and features for time zones, intervals, format, compare and manipulating dates and times.
  
*Example:*
```php
$now = new DateTime();
echo $now->format('Y-m-d H:i:s'); // Output: 2024-11-22 08:28:58 (example)
```

*Example:* DateTime class with timezone
```php
$datetime = new DateTime();
$datetime->setTimezone(new DateTimeZone('Asia/Kolkata'));
echo $datetime->format('Y-m-d h:i:s A'); // Output: 2024-11-22 01:22:11 PM (example)
```

*Example:* Calculating date difference
```php
$date1 = new DateTime('2024-11-22');
$date2 = new DateTime('2025-01-01');
$interval = $date2->diff($date1);
echo $interval->days . " days"; // Output: 40 days
```

### &#10022; DateTimeImmutable Class:
It similar to `DateTime` class, but objects are immutable. And it is useful for preventing accidental modifications to date and time object.

*Example:*
```php
$now = new DateTimeImmutable();
echo $now->format('Y-m-d H:i:s'); // Output: 2024-11-22 08:28:58 (example)
```

### &#10022; DateInterval Class:
It represents a period of time between two dates or times. And it can be used to calculate differences between given dates.

*Example:*
```php
$Datetime = new Datetime('NOW', new DateTimeZone('Asia/Kolkata'));
$Datetime->add(DateInterval::createFromDateString('2 day'));

echo $Datetime->format("Y-m-d H:i:s"); // Output: 2024-11-24 15:44:05 (example)
```

### &#10022; DatePeriod Class:
It represents a sequence of dates and times. And it can be used to iterate over a range of dates or to create recurring events.

*Example:* Calculate Date Range
```php
$start_date = date_create("2024-12-01");
$end_date   = date_create("2025-01-01"); // If you want to include the last date or this date, add 1 day to it

// Create date interval
$interval = DateInterval::createFromDateString('1 day');
// Create date range based on start date, interval and end date
$daterange = new DatePeriod($start_date, $interval ,$end_date);

// Iterate date range
foreach($daterange as $date){
    echo $date->format('d-m-Y') . nl2br("\n");
}

// reverse the date range array
$daterange = array_reverse(iterator_to_array($daterange));

// Iterate date range
foreach($daterange as $date){
    echo $date->format('d-m-Y'). nl2br("\n");
}
```

### &#10022; Formatting Dates and Times:
- `date()` function accepts format specifiers to format dates and times.
- `DateTime` class uses `format()` method to give more flexibility and customization options.

**Common Format Specifiers:**
| Specifier | Description |
|---|---|
| `d` | Day of the month, 2 digits with leading zeros |
| `D` | Day of the week, textual, 3 letters (textual, Mon-Sun) |
| `j` | Day of the month without leading zeros |
| `l` | Day of the week, textual, full length (full textual, Sunday-Saturday) |
| `N` | ISO-8601 numeric representation of the day of the week (1 (Monday) to 7 (Sunday)) |
| `w` | Day of the week (0 (Sunday) to 6 (Saturday)) |
| `z` | Day of the year (0-365) |
| `W` | ISO-8601 week number of year, week starting on Monday (01-53) |
| `F` | Month name, full |
| `m` | Month number, with leading zeros |
| `M` | Month name, 3 letters (textual, Jan-Dec) |
| `n` | Month number without leading zeros |
| `t` | Number of days in the given month |
| `L` | Whether it's a leap year (1 if it is a leap year, 0 otherwise) |
| `Y` | Year with century (e.g., 2024) |
| `y` | Year without century (e.g., 24) |
| `a` | Lowercase AM or PM |
| `A` | Uppercase AM or PM |
| `B` | Swatch Internet Time (000 to 999) |
| `g` | 12-hour format of an hour without leading zeros (1-12) |
| `G` | 24-hour format of an hour without leading zeros (0-23) |
| `h` | 12-hour format of an hour with leading zeros (01-12) |
| `H` | 24-hour format of an hour with leading zeros (00-23) |
| `i` | Minutes |
| `s` | Seconds |
| `u` | Microseconds |
| `e` | Timezone identifier (e.g., UTC, EST, MST) |
| `T` | Timezone abbreviation (e.g., UTC, EST, MST) |
| `O` | Timezone offset in hours (+0200) |
| `Z` | Timezone offset in seconds (+07200) |

### &#10022; Parsing Relative Dates and Times:
*Example:*
```php
$now = strtotime('now');
$specificDate = strtotime('22 November 2024');
$tomorrow = strtotime('tomorrow');
$yesterday = strtotime('-1 day');
$nextWeek = strtotime('+1 week');
$lastMonth = strtotime('-1 month');
$lastSpecificDay = strtotime('last Tuesday');
$specificDay = strtotime('next Thursday')
$specificInterval = strtotime('+1 week 3 days 6 hours 50 seconds');
```

### &#10022; Date and Time Constants:
PHP provides built-in constants to represent common date and time format and values. Date and time constants are useful for various calculations and comparisons.

**Date and Time Constants:**
- `DATE_ATOM`: Atom format (YYYY-MM-DDTHH:MM:SS+00:00)
- `DATE_COOKIE`: Cookie format (Friday, 22-Nov-2024 14:48:45 GMT)
- `DATE_ISO8601`: ISO-8601 format (YYYY-MM-DDTHH:MM:SS+00:00)
- `DATE_RFC822`: RFC 822 format (Fri, 22 Nov 2024 14:48:45 +0100)
- `DATE_RFC850`: RFC 850 format (Friday, 22-Nov-24 14:48:45 GMT)
- `DATE_RFC1036`: RFC 1036 format (Friday, 22-Nov-24 14:48:45 GMT)
- `DATE_RFC1123`: RFC 1123 format (Fri, 22 Nov 2024 14:48:45 GMT)
- `DATE_RSS`: RSS format (Fri, 22 Nov 2024 14:48:45 +0100)
- `DATE_W3C`: W3C format (2024-11-22T14:48:45+01:00)

**Use cases:**
| Constant | Format | Use Case |
|---|---|---|
| `DATE_ATOM` | YYYY-MM-DDTHH:MM:SS+00:00 | Used in RSS feeds, Atom feeds, and other XML-based formats. |
| `DATE_COOKIE` | Friday, 22-Nov-2024 14:48:45 GMT | Used in HTTP cookies. |
| `DATE_ISO8601` | YYYY-MM-DDTHH:MM:SS+00:00 | International standard date and time format. |
| `DATE_RFC822` | Fri, 22 Nov 2024 14:48:45 +0100 | Used in email headers and other RFC 822 compliant formats. |
| `DATE_RFC850` | Friday, 22-Nov-24 14:48:45 GMT | Older RFC format. |
| `DATE_RFC1036` | Friday, 22-Nov-24 14:48:45 GMT | Older RFC format. |
| `DATE_RFC1123` | Fri, 22 Nov 2024 14:48:45 GMT | More recent RFC format. |
| `DATE_RSS` | Fri, 22 Nov 2024 14:48:45 +0100 | Used in RSS feeds. |
| `DATE_W3C` | 2024-11-22T14:48:45+01:00 | W3C standard date and time format. |

*Example:*
```php
$date = date(DATE_RFC822);
echo $date; // Output: Fri, 22 Nov 24 14:51:58 +0530 (example)

$now = time();
echo date(DATE_ATOM, $now) . nl2br("\n"); // Output: 2024-11-22T14:55:24+05:30 (example)
echo date(DATE_COOKIE, $now) . nl2br("\n"); // Output: Friday, 22-Nov-2024 14:55:24 IST (example)
echo date(DATE_ISO8601, $now) . nl2br("\n"); // Output: 2024-11-22T14:55:24+0530 (example)
```

### &#10022; Timezones:
Time zones are geographic regions that has uniform standard time on the region. PHP has built-in functions and classes to handle time zones.

- Setting Timezone: 

It sets default timezone for all date and time functionalities.

*Syntax:*

`date_default_timezone_set()`

*Example:*
```php
date_default_timezone_set('Asia/Kolkata');
```

- Get list of timezones: 

It returns a list of all supported timezones.
*Syntax:*

`timezone_identifiers_list()`

*Example:*
```php
$timezones = timezone_identifiers_list();
print_r($timezones);
```

- Represent a timezone: 

It represents a specific timezone. It can be used to create `DateTime` objects with specific timezones.

*Syntax:*

`DateTimeZone('Timezone')`

*Example:*
```php
$timezone = new DateTimeZone('Asia/Kolkata');
$dateTime = new DateTime('now', $timezone);
echo $dateTime->format('Y-m-d h:i:s A'); // Output: 2024-11-22 01:22:11 PM (example)
```
- Converting Between Timezones:

```php
$dateTime = new DateTime('now', new DateTimeZone('America/Los_Angeles'));
echo $dateTime->format('Y-m-d h:i:s A'); // Output: 2024-11-21 11:56:23 PM (example)
echo nl2br('\n');
$dateTime->setTimezone(new DateTimeZone('Asia/Kolkata'));
echo $dateTime->format('Y-m-d h:i:s A'); // Output: 2024-11-22 01:26:23 PM (example)
```

- Daylight Saving Time (DST): 

Handles DST transitions for specific timezone using the `getOffset()` method.

*Example:*
```php
$dateTime = new DateTime('now', new DateTimeZone('Asia/Kolkata'));
$offset = $dateTime->getOffset();
echo $offset; // Output: 19800 (in seconds)
```

- Time Difference between Two Timezones:

*Example:*
```php
// Timezone 1
$timezone1 = new DateTimeZone('Asia/Kolkata');
$datetime1 = new DateTime('now', $timezone1);

// Timezone 2
$timezone2 = new DateTimeZone('America/Los_Angeles');
$datetime2 = new DateTime('now', $timezone2);

// Calculate the difference
$interval = $datetime1->diff($datetime2);

// Extract hours and minutes
$hours = $interval->h;
$minutes = $interval->i;

echo "Time difference: $hours hours $minutes minutes";
```

### &#10022; Key Points:
- Explicit Timezone Setting: Always set the default timezone or specify timezones when handling date and time related process to avoid unexpected behavior.
- Consider Daylight Saving Time (DST): Use DST transitions and their impact on calculations.
- Use Appropriate Timezone Identifiers:Refer IANA Time Zones for accurate timezone identifiers.
- Validate User Input: When working with user-provided dates, time and timezones, Validate data to prevent any unexpected imperfections and vulnerabilities.

---
[&#8682; To Top](#-date-and-time)

[&#10094; Previous Topic](./forms-and-data-handling.md) &emsp; [Next Topic &#10095;](./numbers-and-currencies.md)

[&#8962; Goto Home Page](../README.md)