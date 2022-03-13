# gnuplot-windows-C
Small guide on how to use gnuplot for plotting (and more) when programming in C on windows

***********************************************************
IMPORTANT: 
I did not make this solution, I found it on stackoverflow at this link: https://stackoverflow.com/questions/9349538/gnuplot-c-from-windows-command-window-opens-and-closes/14027358#14027358

The reason why I'm writing the solution here is because I wanted to save it on github in case I'd need it again in the future, and also because maybe other people with the same problem can find this solution. All the credits go to the dude that answered in the link above.
***********************************************************


This txt file briefly explains how to plot data using gnuplot in Windows WHEN PROGRAMMING IN C.
It basicaly makes use of pipelines. Below is a simple code that shows how to do it, with different examples.

FILE* pipe = _popen("C:/Programs/gnuplot/bin/gnuplot.exe -persist", "w");
	if (pipe != NULL)
	{
		fprintf(pipe, "plot 'data.dat' with linespoints linestyle 1 \n");

		/*
		fprintf(pipe, "plot(x, sin(x))\n"); //a simple example function
		fprintf(pipe, "set term pngcairo\n");
		fprintf(pipe, "set output \"myFile.png\"\n");
		fprintf(pipe, "replot\n");
		fprintf(pipe, "set term win\n");
		*/

		fflush(pipe);
	}
	else puts("Could not open the file\n");
	_pclose(pipe);


Note: the "-persist" command in line 14 keeps the plotting window open. If you don't need it you can safely remove it.
