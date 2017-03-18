# RPG_game

## Part 1 - RPG Game: Creating the window

In this first part, we will create the window of our RPG Game, following the next steps: 
* We create a new java project
* Using our SRC file, we create a new package (to better organize our future classes and also our principal class)

#### Step 1 : Creating our principal class and converting it into a Canvas
A Canvas component represents a blank rectangular area of the screen onto which the application can draw or from which the application can trap input events from the user. 

Source: https://docs.oracle.com/javase/7/docs/api/java/awt/Canvas.html

That means, we will inherit our principal class from the Canvas class:
* Importing the Canvas class, using the awt toolkit in order to build the window
* Adding a default serial version ID, so we let know java later if we are using the same class or if it has changed

```java 
import java.awt.Canvas;

public class Game extends Canvas {

	private static final long serialVersionUID = 1L;

}
```

Is important to know that the Canvas is the component but not the window, so we need to create it.

#### Step 2 : Creating the window

A frame (implemented as an instance of the JFrame class) is a window that has decorations such as a border, a title, and supports button components that close or iconify the window.

Source: http://docs.oracle.com/javase/tutorial/uiswing/components/frame.html

So as we will be using only one window in our class Game, we need to:
* Use a private static JFrame. Why static ? Because in the case of the JFrame we don't need to create instances and also, it means there's only one type of this variable inside our class Game. 
* Import the JFrame
* Create a new instance private Game() from the class Game in which all the content of the constructor will be run. Why private ? Because for the moment, only the class Game will be able to create instances.

```java 
import java.awt.Canvas;

import javax.swing.JFrame;

public class Game extends Canvas {

	private static final long serialVersionUID = 1L;
	
	private static JFrame window;
	
	private Game() {
	
	}

}
```

#### Step 3 : Window dimension

Now, we will define the dimension of the window using 2 int, allowing us to change it more easily later if necessary. 

* Width = 800
* Heigth = 800

```java 
import java.awt.Canvas;

import javax.swing.JFrame;

public class Game extends Canvas {

	private static final long serialVersionUID = 1L;
	
	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre
	
	private static JFrame window;
	
	private Game() {
	
	}

}
```

Final means they won't change during the whole execution of the program (letting us also to have a more efficient game). Also, we write WIDTH and HEIGHT in uppercase because they are constant variables (their value won't change).

#### Step 4 : Creating the constructor

In order to fix the size that we would like to have in our window, we will need to: 
* Use the method setPreferredSize() 
* Give it a new Dimension : WIDTH and HEIGHT.
* Import Dimension

```java 
import java.awt.Canvas;
import java.awt.Dimension;

import javax.swing.JFrame;

public class Game extends Canvas {

	private static final long serialVersionUID = 1L;
	
	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre
	
	private static JFrame window;
	
	private Game() {
	
	setPreferredSize(new Dimension(WIDTH, HEIGHT));
	
	}

}
```

#### Step 5 : Initializing our window object

To initialize our window object, we will: 
* Use window = new JFrame () 
* Give it a name, defining a new constant variable: private static final String NAME = "Game"

```java 
import java.awt.Canvas;
import java.awt.Dimension;

import javax.swing.JFrame;

public class Game extends Canvas {

	private static final long serialVersionUID = 1L;
	
	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre
	
	private static final String NAME = "Game";
	
	private static JFrame window;
	
	private Game() {
	
	setPreferredSize(new Dimension(WIDTH, HEIGHT));
	
		window = new JFrame(NAME);
	
	}

}
```

#### Step 6 : Closing the program application when closing the window and resizing specifications

In this step we will need to : 

* Set a default close operation because if we don't, once we close the window we created, the program will still running
* We add a JFrame.EXIT_ON_CLOSE to prevent all this
* We need to unable the users to resize the window dimension, using window.setResizable(false)

```java 
import java.awt.Canvas;
import java.awt.Dimension;

import javax.swing.JFrame;

public class Game extends Canvas {

	private static final long serialVersionUID = 1L;
	
	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre
	
	private static final String NAME = "Game";
	
	private static JFrame window;
	
	private Game() {
	
	setPreferredSize(new Dimension(WIDTH, HEIGHT));
	
		window = new JFrame(NAME);
		window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		window.setResizable(false);
	}

}
```

#### Step 7 : Adding the Canvas class to the window and adjusting the content according to the window

A layout manager is an object that implements the LayoutManager interface and determines the size and position of the components within a container. Although components can provide size and alignment hints, a container's layout manager has the final say on the size and position of the components within the container.

Source: http://docs.oracle.com/javase/tutorial/uiswing/layout/using.html

In this step we will need to : 

* Add an intern organisation of the window (set a Layout and it's manager), using window.setLayout(new BorderLayout())
* Import BorderLayout
* Add our Canvas class in the center of the window, using window.add(this, BorderLayout.CENTER)
* Adjust the content of our window (according to the window dimension 800x600), using window.pack()

```java 
import java.awt.BorderLayout;
import java.awt.Canvas;
import java.awt.Dimension;

import javax.swing.JFrame;

public class Game extends Canvas {

	private static final long serialVersionUID = 1L;
	
	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre
	
	private static final String NAME = "Game";
	
	private static JFrame window;
	
	private Game() {
	
	setPreferredSize(new Dimension(WIDTH, HEIGHT));
	
		window = new JFrame(NAME);
		window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		window.setResizable(false);
		window.setLayout(new BorderLayout());
		window.add(this, BorderLayout.CENTER);
		window.pack();
	}

}
```

#### Step 8 : Adjusting the position of the window and showing it

In this step we will need to:

* Adjust the position of the window (set it's location in the center) according or relative to the desktop, using window.setLocationRelativeTo(null)
* Make the window visible once we run the program, using window.setVisible(true) 

```java 
import java.awt.BorderLayout;
import java.awt.Canvas;
import java.awt.Dimension;

import javax.swing.JFrame;

public class Game extends Canvas {

	private static final long serialVersionUID = 1L;
	
	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre
	
	private static final String NAME = "Game";
	
	private static JFrame window;
	
	private Game() {
	
	setPreferredSize(new Dimension(WIDTH, HEIGHT));
	
		window = new JFrame(NAME);
		window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		window.setResizable(false);
		window.setLayout(new BorderLayout());
		window.add(this, BorderLayout.CENTER);
		window.pack();
		window.setLocationRelativeTo(null);
		window.setVisible(true);
	}

}
```

#### Step 9 : The main method

The main method will allow us to indicate java where it needs to start reading our program. For this, we will need to:

* Create an instance of our Game class, using public static void main (String[] args) {
Game game = new Game ();
}

```java 
package game;

import java.awt.BorderLayout;
import java.awt.Canvas;
import java.awt.Dimension;

import javax.swing.JFrame;

public class Game extends Canvas {

	private static final long serialVersionUID = 1L;

	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre

	private static final String NAME = "Game";

	private static JFrame window;

	private Game() {

		setPreferredSize(new Dimension(WIDTH, HEIGHT));

		window = new JFrame(NAME);
		window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		window.setResizable(false);
		window.setLayout(new BorderLayout());
		window.add(this, BorderLayout.CENTER);
		window.pack();
		window.setLocationRelativeTo(null);
		window.setVisible(true);
	}

	public static void main(String[] args) {
		Game game = new Game();
	}
}
```

## Part 2 - RPG Game: Multithreading

Before we talk about multithreading, let’s discuss threads. 

A thread is a light-weight smallest part of a process that can run concurrently with the other parts(other threads) of the same process. Threads are independent because they all have separate path of execution that’s the reason if an exception occurs in one thread, it doesn’t affect the execution of other threads. All threads of a process share the common memory. The process of executing multiple threads simultaneously is known as multithreading.

Source: http://beginnersbook.com/2013/03/multithreading-in-java/

Until now, we have been using the main thread. 

When a Java program starts up, one thread begins running immediately. This is usually called the main thread, because it is the one that is executed when your program begins.

But in the RPG Game we will need to use a second thread, in order to run automatically our game, draw its graphics, etc. So to achieve this, we will need to:

* Create an interface in charge of running different threads using implements Runnable (which is an abstract method) and add the method run (this method will run our second thread)
* We have to create the second thread, using private static Thread and giving the name thread to it
* Define and initialize the thread using 2 methods: private void start() and private void stop() 
* In the method start() we will initialize a new object thread = new Thread(this, "graphics") and then execute it using thread.start()
* Initialize the method start() into the main using game.start()

From this point, everything that is contained in the run method will be executed sequencially. 

```java 
package game;

import java.awt.BorderLayout;
import java.awt.Canvas;
import java.awt.Dimension;

import javax.swing.JFrame;

public class Game extends Canvas implements Runnable {

	private static final long serialVersionUID = 1L;

	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre

	private static final String NAME = "Game";

	private static JFrame window;
	private static Thread thread;

	private Game() {

		setPreferredSize(new Dimension(WIDTH, HEIGHT));

		window = new JFrame(NAME);
		window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		window.setResizable(false);
		window.setLayout(new BorderLayout());
		window.add(this, BorderLayout.CENTER);
		window.pack();
		window.setLocationRelativeTo(null);
		window.setVisible(true);
	}

	public static void main(String[] args) {
		Game game = new Game();
		game.start();
	}

	private void start() {
		thread = new Thread(this, "graphics");
		thread.start();
	}

	private void stop() {

	}

	public void run() {
		System.out.print("thread 2 is working");
	}
}
```

## Part 3 - RPG Game: Game Loop

The while statement continually executes a block of statements while a particular condition is true. 
Using this method at this point is important because it will allow us to run indefinitely 2 methods, one of them, in charge of giving us the updates of the game, and the other one, will be drawing the graphics of it.  

So here, we will need to: 
* Create a boolean that tell us if the game is running or not (initialized as false by default) using : private static boolean workingWell = false
* Initialize it as true into the start method (before the second thread) and as false into the stop method, using: workingWell = true and workingWell = false
* Create the while statement into the main method
* Add the reserved word volatile into the boolean
* Add the word synchronized into the 2 methods we are using: start and stop

Using volatile variables reduces the risk of memory consistency errors, because any write to a volatile variable establishes a happens-before relationship with subsequent reads of that same variable. This means that changes to a volatile variable are always visible to other threads. What's more, it also means that when a thread reads a volatile variable, it sees not just the latest change to the volatile, but also the side effects of the code that led up the change.

Source: https://docs.oracle.com/javase/tutorial/essential/concurrency/atomic.html

* Use a try catch in order to stop our thread in the stop method, letting us to know if there's an error via the console and not showing the errors to the user.

Why use join and not stop ? We use thread.join because if we were using thread.stop the program will terminate or end abruptly our thread. In the other hand, using join, it allow us to wait until everything is finished inside the thread and then stop.

```java 
package game;

import java.awt.BorderLayout;
import java.awt.Canvas;
import java.awt.Dimension;

import javax.swing.JFrame;

public class Game extends Canvas implements Runnable {

	private static final long serialVersionUID = 1L;

	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre

	private static volatile boolean workingWell = false;

	private static final String NAME = "Game";

	private static JFrame window;
	private static Thread thread;

	private Game() {

		setPreferredSize(new Dimension(WIDTH, HEIGHT));

		window = new JFrame(NAME);
		window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		window.setResizable(false);
		window.setLayout(new BorderLayout());
		window.add(this, BorderLayout.CENTER);
		window.pack();
		window.setLocationRelativeTo(null);
		window.setVisible(true);
	}

	public static void main(String[] args) {
		Game game = new Game();
		game.start();
	}

	private synchronized void start() {
		workingWell = true; // we put the boolean before creating the object
							// thread to prevent bugs with the run method that
							// use the thread too

		thread = new Thread(this, "graphics");
		thread.start();
	}

	private synchronized void stop() {
		workingWell = false;

		try {
			thread.join();
		} catch (InterruptedException e) {
			e.printStackTrace();
		}

	}

	public void run() {
		// System.out.print("thread 2 is working");
		while (workingWell) {

		}
	}
}
```

## Part 4 - RPG Game: Timer and FPS counter
We will start by creating 2 methods that will be in charge of controlling almost all the content of the game (variables and graphics):
* private void update(), method in which we will put all the variables related with the life of the game characters, etc
* private void showing(), method in which we will put all the necessary methods in order to show all the graphics

Then, we need to include them into the method run (inside the while statement) which as we know, will run our second thread.

Once we do that, we will need to create a timer. Why ? Because if we want the game to works uniformly in every computer, we should run these 2 methods (update and showing) at a specific number of times so we could be able to control it.

In order to achieve this, we will need to use: 
* The method System.nanoTime()

The advantage of using this method is that it counts in nano seconds (taking the number of clock cycles processor CPU as reference) and it doesn't depend on the operating system but the microprocessor.

1 Second = 1,000,000,000 Nanoseconds

Having this in mind, we will create some variables in order to define :
* The equivalent of nanoseconds per second, using final int NS_PER_SECOND = 1000000000;
* The objective of the number of times we want to update per second, using final byte UPS_OBJECTIVE = 60;
* Calculating how many nanoseconds we must need in every update, using final double NS_PER_UPDATE = NS_PER_SECOND / UPS_OBJECTIVE;

NS= Nanoseconds

UPS= Updates per second

We use final because it means they won't change during the whole execution of the program, so it will starts in every start of the loop. Then, in order to give or atribute a number of nanoseconds given in a specific moment or instant, we will need to use:
* long updateReference = System.nanoTime();

In graphics programming, the term Delta is usually used for variably updating scenery based on the elapsed time since the game last updated. Source: https://en.wikipedia.org/wiki/Delta_timing

We will:
* Stock inside Delta, the result of dividing the time lapsed between the nanoseconds per update. And if it comply the condition (be superior or equal to 1) it will run the while statement. So, while Delta is = or superior to 1 it will update the game and then sustract 1 to delta. This means the game will update exactly 60 times per second.

Once we have done all this, we will create:
* an UPS counter
* a FPS counter 
* show them in the title of the window of the game

So until now, the code looks like this : 

```java 

package game;

import java.awt.BorderLayout;
import java.awt.Canvas;
import java.awt.Dimension;

import javax.swing.JFrame;

public class Game extends Canvas implements Runnable {

	private static final long serialVersionUID = 1L;

	private static final int WIDTH = 800; // largeur de la fenetre
	private static final int HEIGHT = 600; // hauteur de la fenetre

	private static volatile boolean workingWell = false;

	private static final String NAME = "Game";

	private static int ups = 0;
	private static int fps = 0;

	private static JFrame window;
	private static Thread thread;

	private Game() {

		setPreferredSize(new Dimension(WIDTH, HEIGHT));

		window = new JFrame(NAME);
		window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		window.setResizable(false);
		window.setLayout(new BorderLayout());
		window.add(this, BorderLayout.CENTER);
		window.pack();
		window.setLocationRelativeTo(null);
		window.setVisible(true);
	}

	public static void main(String[] args) {
		Game game = new Game();
		game.start();
	}

	private synchronized void start() {
		workingWell = true; // we put the boolean before creating the object
							// thread to prevent bugs with the run method that
							// use the thread too

		thread = new Thread(this, "graphics");
		thread.start();
	}

	private synchronized void stop() {
		workingWell = false;

		try {
			thread.join();
		} catch (InterruptedException e) {
			e.printStackTrace();
		}

	}

	private void update() {
		ups++;
	}

	private void showing() {
		fps++;
	}

	public void run() {
		// System.out.print("thread 2 is working");

		final int NS_PER_SECOND = 1000000000;
		final byte UPS_OBJECTIVE = 60;
		final double NS_PER_UPDATE = NS_PER_SECOND / UPS_OBJECTIVE;

		long updateReference = System.nanoTime();
		long counterReference = System.nanoTime();

		double timeLapsed;
		double delta = 0;

		while (workingWell) {
			final long startLoop = System.nanoTime(); // initializing the
														// chronometer

			timeLapsed = startLoop - updateReference; // calculates the time
														// lapsed between both
														// system.nanoTimes
			updateReference = startLoop;

			delta += timeLapsed / NS_PER_UPDATE;

			while (delta >= 1) {
				update();
				delta--; // equivalent to delta = delta - 1
			}

			showing();

			if (System.nanoTime() - counterReference > NS_PER_SECOND) {
				window.setTitle(NAME + " || APS:" + ups + " || FPS:" + fps);
				ups = 0;
				fps = 0;
				counterReference = System.nanoTime();
			}
		}
	}
}

```

## Part 5 - RPG Game: Sprite Sheet

A sprite is a single graphic image that is incorporated into a larger scene so that it appears to be part of the scene. Sprites are a popular way to create large, complex scenes as you can manipulate each sprite separately from the rest of the scene. This allows for greater control over how the scene is rendered, as well as over how the players can interact with the scene.

It is not uncommon for games to have tens to hundreds of sprites. Loading each of these as an individual image would consume a lot of memory and processing power. To help manage sprites and avoid using so many images, many games use spritesheets. When you put many sprites into a single image, you get a spritesheet. Spritesheets are used to speed up the process of displaying images to the screen; It is much faster to fetch one image and display only a part of that image than it is to fetch many images and display them.

Source:https://gamedevelopment.tutsplus.com/tutorials/an-introduction-to-spritesheet-animation--gamedev-13099

So, in this part we will:
* Create a new package called graphics and inside it, we are going to create a new class SpriteSheet
* Use a collection (array) of pixels: public final int[] pixels
* Create an image using a location path and getting the RGB of it

Code will look like this : 

```java 
package graphics;

import java.awt.image.BufferedImage;
import java.io.IOException;

import javax.imageio.ImageIO;

public class SpriteSheet {
	private final int width;
	private final int height;
	public final int[] pixels;

	// constructor
	public SpriteSheet(final String path, final int width, final int height) {
		this.width = width; // this.width in reference to the variable width,
							// and = width in reference to the temporal value
							// from the constructor
		this.height = height; // this.width in reference to the variable height,
								// and = height in reference to the temporal
								// value from the constructor

		pixels = new int[width * height];

		BufferedImage image;
		try {
			image = ImageIO.read(SpriteSheet.class.getResource(path));

			image.getRGB(0, 0, width, height, pixels, 0, width); // start x,
																	// start y ,
																	// array,
																	// offset,
																	// scansize

		} catch (IOException e) {
			e.printStackTrace();
		}

	}
}

```
