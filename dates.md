#DATETIME() - quelques exemples


```php
$now=new DateTime();
echo $now->format('d m Y     H:i'); 	

$today=new DateTime();

$yesterday= new DateTime();
$yesterday->modify('- 1 days');
$yesterday=$yesterday->format('Y-m-d');

$thisMonthFirstDay=new DateTime('first day of this month');
$thisMonthFirstDay=$thisMonthFirstDay->format('Y-m-D');

// le mois dernier à la même date (qu'hier)
$lastMonth=new DateTime();
$lastMonth->modify('- 1 months');
$lastMonth->modify('- 1 days');
$lastMonth=$lastMonth->format('Y-m-d');


$lastMonthFirstDay=new DateTime('first day of last month');
$lastMonthFirstDay=$lastMonthFirstDay->format('Y-m-d');



http://php.net/manual/fr/datetime.formats.relative.php
http://php.net/manual/fr/datetime.construct.php


/week 01
$mondayWeekOne=new DateTime('Monday this week');
$mondayWeekOne->modify('+' .$addWeek .' week');
$startDayOne=$mondayWeekOne->format('d');
$mondayWeekOne=$mondayWeekOne->format('Y-m-d');

$fridayWeekOne=new DateTime('friday this week');
$fridayWeekOne->modify('+' .$addWeek .' week');
$endDayOne=$fridayWeekOne->format('d');
$monthOne=$fridayWeekOne->format('n');
$monthOne=$months[$monthOne];
$fridayWeekOne=$fridayWeekOne->format('Y-m-d');



//week 02
$addWeek++;
$mondayWeekTwo=new DateTime('Monday this week');
$mondayWeekTwo->modify('+' .$addWeek .' week');
$startDayTwo=$mondayWeekTwo->format('d');
$mondayWeekTwo=$mondayWeekTwo->format('Y-m-d');

$fridayWeekTwo=new DateTime('friday this week');
$fridayWeekTwo->modify('+' .$addWeek .' week');
$endDayTwo=$fridayWeekTwo->format('d');
$monthTwo=$fridayWeekTwo->format('n');
$monthTwo=$months[$monthTwo];
$fridayWeekTwo=$fridayWeekTwo->format('Y-m-d');




//week 03
$addWeek++;
$mondayWeekThree=new DateTime('Monday this week');
$mondayWeekThree->modify('+' .$addWeek .' week');
$startDayThree=$mondayWeekThree->format('d');
$mondayWeekThree=$mondayWeekThree->format('Y-m-d');

$fridayWeekThree=new DateTime('friday this week');
$fridayWeekThree->modify('+' .$addWeek .' week');
$endDayThree=$fridayWeekThree->format('d');
$monthThree=$fridayWeekThree->format('n');
$monthThree=$months[$monthThree];
$fridayWeekThree=$fridayWeekThree->format('Y-m-d');

```

