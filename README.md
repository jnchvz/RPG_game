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

