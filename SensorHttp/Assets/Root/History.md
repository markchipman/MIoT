﻿Title: History
Author: Peter Waher
Description: This page displays historical values of the sensor.
Cache-Control: max-age=0, no-cache, no-store
Master: Menu.md

Historical values
============================

The following graphs display historical values of the sensor.

Minutes
-------------

{
DrawGraph(Records):=
(
	MinTP:=Records.MinLightAt;
	Min:=Records.MinLight;
	MaxTP:=Records.MaxLightAt;
	Max:=Records.MaxLight;
	TP:=join(MinTP, reverse(MaxTP));
	Values:=join(Min, reverse(Max));
	plot2darea(Records.Timestamp, Records.AvgMovement, "Green")+
		polygon2d(TP, Values, rgba(0,0,255,32))+
		plot2dline(Records.Timestamp, Records.AvgLight, "Red");
);
DrawGraph(SensorHttp.App.GetLastMinutes());
}


Hours
-------------

{DrawGraph(SensorHttp.App.GetLastHours());}


Days
-------------

{DrawGraph(SensorHttp.App.GetLastDays());}