moderngl_camera
===============

a quaternion based camera for modernGL


##Using with GLUT
In order to use this code with the GLUT library a few more functions are required, it is assumed that camera is a Camera object. 

<pre>
//Camera camera
void CallBackKeyboardFunc(unsigned char key, int x, int y)
{
	switch (key) {
	case 'w':
		camera.Move(FORWARD);
		break;
	case 'a':
		camera.Move(LEFT);
		break;
	case 's':
		camera.Move(BACK);
		break;
	case 'd':
		camera.Move(RIGHT);
		break;
	case 'q':
		camera.Move(DOWN);
		break;
	case 'e':
		camera.Move(UP);
		break;
	}
}

void CallBackMouseFunc(int button, int state, int x, int y)
{
	camera.SetPos(button, state, x, y);
}
void CallBackMotionFunc(int x, int y)
{
	camera.Move2D(x, y);
}
</pre>
