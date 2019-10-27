# poll for Windows Visual-C++
poll with WSA library


use with something like that :

#ifdef _WIN32

static int nbSocket = 0;
static int yetDone  = 0;

//before using sockets
void initWSA()
{
	if(!yetDone)
	{
		yetDone = 1;
		initiateWSA();
	}
}

//when a socket is open do not forget
  nbSocket++;

//after using a socket
void clearWSA()
{
	nbSocket = nbSocket - 1;
	if(nbSocket == 0)
  {
		WSACleanup();
    yetDone = 0;
  }
}

#endif

The poll function code can be found in the poll.zip file
