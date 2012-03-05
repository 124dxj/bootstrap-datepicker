# Home

http://www.eyecon.ro/bootstrap-datepicker/

# Example

Attached to a field with the format specified via options:

    :::html
    <input type="text" value="02-16-2012" id="datepicker">  
######
    :::javascript
    $('#datepicker').datepicker({
        format: 'mm-dd-yyyy'
    });

Attached to a field with the format specified via data tag:

    :::html
    <input type="text" value="02/16/12" data-date-format="mm/dd/yy" id="datepicker" >
######
    :::javascript
    $('#datepicker').datepicker();

As component:

    :::html
    <div class="input-append date" id="datepicker" data-date="12-02-2012" data-date-format="dd-mm-yyyy">
        <input size="16" type="text" value="12-02-2012" readonly>
        <span class="add-on"><i class="icon-th"></i></span>
    </div>
######
    :::javascript
    $('#datepicker').datepicker();

Attached to non-field element, using events to work with the date values.

    :::html
    <div class="alert alert-error" id="alert">
        <strong>Oh snap!</strong>
    </div>
    <table class="table">
        <thead>
            <tr>
              <th>
                  Start date
                  <a href="#" class="btn small" id="date-start" data-date-format="yyyy-mm-dd" data-date="2012-02-20">Change</a>
              </th>
              <th>
                  End date
                  <a href="#" class="btn small" id="date-end" data-date-format="yyyy-mm-dd" data-date="2012-02-25">Change</a>
              </th>
            </tr>
        </thead>
        <tbody>
            <tr>
              <td id="date-start-display">2012-02-20</td>
              <td id="date-end-display">2012-02-25</td>
            </tr>
        </tbody>
    </table>
######
    :::javascript
    var startDate = new Date(2012,1,20);
    var endDate = new Date(2012,1,25);
    $('#date-start')
        .datepicker()
        .on('changeDate', function(ev){
            if (ev.date.valueOf() > endDate.valueOf()){
                $('#alert').show().find('strong').text('The start date must be before the end date.');
            } else {
                $('#alert').hide();
                startDate = new Date(ev.date);
                $('#date-start-display').text($('#date-start').data('date'));
            }
            $('#date-start').datepicker('hide');
        });
    $('#date-end')
        .datepicker()
        .on('changeDate', function(ev){
            if (ev.date.valueOf() < startDate.valueOf()){
                $('#alert').show().find('strong').text('The end date must be after the start date.');
            } else {
                $('#alert').hide();
                endDate = new Date(ev.date);
                $('#date-end-display').text($('#date-end').data('date'));
            }
            $('#date-end').datepicker('hide');
        });
    });


# Using bootstrap-datepicker.js

Call the datepicker via javascript:

    :::javascript
    $('.datepicker').datepicker()

## Options

### format

String.  Default: 'mm/dd/yyyy'

The date format, combination of d, dd, m, mm, yy, yyy.

### weekStart

Integer.  Default: 0

Day of the week start. 0 (Sunday) to 6 (Saturday)

## Markup

Format a component.

    :::html
    <div class="input-append date" id="datepicker" data-date="12-02-2012" data-date-format="dd-mm-yyyy">
        <input class="span2" size="16" type="text" value="12-02-2012">
        <span class="add-on"><i class="icon-th"></i></span>
    </div>

## Methods

### .datepicker(options)

Initializes an datepicker.

## Events

Datepicker class exposes a few events for manipulating the dates.

### show

Fired when the date picker is displayed.

### hide

Fired when the date picker is hidden.

### changeDate

Fired when the date is changed.

    :::javascript
    $('#date-end')
        .datepicker()
        .on('changeDate', function(ev){
            if (ev.date.valueOf() < date-start-display.valueOf()){
                ....
            }
        });

