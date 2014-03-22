Modern OpenGL Camera
===============

A quaternion based camera for modern OpenGL using [GLM](http://glm.g-truc.net/)

Code is contained in two files, camera.h and camera.cpp

An example is provided in example.cpp
Use Cmake to compile example

##Using with GLUT

In order to use this code with the GLUT library the following code can be used/adapted.
(A more complete example is provided in example.cpp)

<pre>
Camera camera;
...
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

void DisplayFunc() {
	glEnable(GL_CULL_FACE);
	glClearColor(0.1f, 0.1f, 0.1f, 1.0f);
	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
	glViewport(0, 0, window.size.x, window.size.y);

	glm::mat4 model, view, projection;
	camera.Update();
	camera.GetMatricies(projection, view, model);

	glm::mat4 mvp = projection* view * model;	//Compute the mvp matrix
	glLoadMatrixf(glm::value_ptr(mvp));
	...
	//Draw stuff here
	...
	glutSwapBuffers();
}

int main(int argc, char * argv[]) {
	...
	//GLUT init
	...
	glutDisplayFunc(DisplayFunc);
	glutMouseFunc(CallBackMouseFunc);
	glutMotionFunc(CallBackMotionFunc);
	glutKeyboardFunc(KeyboardFunc);
	
	camera.SetPosition(glm::vec3(0, 0, -1));
	camera.SetLookAt(glm::vec3(0, 0, 0));
	camera.SetClipping(.1, 1000);
	camera.SetFOV(45);
		
	...
}
</pre>

