# Lab-Assignment-4
/**
1. Implement a class Clock whose getHours and getMinutes methods return the current
time at your location. (Call java.time.Instant.now().toString() or, if you are not using
Java 8, new java.util.Date().toString() and extract the time from that string.) Also
provide a getTime method that returns a string with the hours and minutes by calling
the getHours and getMinutes methods. Provide a subclass WorldClock whose constructor
accepts a time offset. For example, if you live in California, a new WorldClock(3) should
show the time in New York, three time zones ahead. Which methods did you over-
ride? (You should not override getTime.)             
**/
Solution:

/*
Super class
 */
public class Clock
{
    String AlarmHour;
    String AlarmMinute;

    public String getAlarmHour()
    {
        String hours=java.time.LocalTime.now().toString().substring(0,2);
        return hours;
    }

    public String getAlarmMinute()
    {
        String min=java.time.LocalTime.now().toString().substring(3,5);
        return min;
    }
    public String getTime()
    {
        String time=getAlarmHour()+":"+getAlarmMinute();
        return time;
    }

    public void  setAlarm(String hour,String minute)
    {
        AlarmHour=hour;
        AlarmMinute=minute;
    }


}

/*
Sub-class
*/
public class WordClock extends Clock
{
    int timeZone=0;

    public WordClock(int timeZone) {
        super();
        this.timeZone = timeZone;
    }



    public String getHours(){
        String Hours=String.valueOf(Integer.parseInt(super.getAlarmHour())+timeZone);
        return Hours;
    }

}

/**
 Program Runner class
 **/
 
 import java.util.Scanner;
public class Runner
{
    public static void main(String[]args)
    {
        Clock MyClock=new Clock();
        System.out.println("My Time:"+MyClock.getTime());

        Scanner input=new Scanner(System.in);

        System.out.println("How many hours Ahead is your timezone");

        int timezone= input.nextInt();
        WordClock ob = new WordClock(timezone);

        String time = ob.getTime();
        System.out.println("MY time +"+ timezone+":"+time);
    }

}

 







