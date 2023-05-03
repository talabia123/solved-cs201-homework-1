Download Link: https://assignmentchef.com/product/solved-cs201-homework-1
<br>
In this homework, you will implement a music album collection system to store the song names of the music albums in a particular collection. For each music album, you will store its artist, its title, its year, and its list of songs. In your implementation, the collection of music albums and the list of songs in each music album will need to be implemented using <strong>dynamically allocated arrays</strong>. The homework has two parts whose requirements are explained below. <strong> </strong>

<h1>PART A:</h1>

<strong> </strong>

<strong>To take the final exam, you must submit this part and receive at least half of its points. </strong>

<strong> </strong>

This part is a simplified version of the entire system. It stores the artists, titles, and years of music albums in a collection without their list of songs. The music albums will be stored in a dynamically allocated array of MusicAlbum objects. Thus, you will first implement the MusicAlbum class. This class is rather simple for Part A, but will need to be extended for Part B.




<ol>

 <li>Below is the required part of the MusicAlbum The name of the class should be MusicAlbum; the interface for the class:</li>

</ol>

<table width="545">

 <tbody>

  <tr>

   <td width="545">#ifndef __SIMPLE_MUSIC_ALBUM_H#define __SIMPLE_MUSIC_ALBUM_H #include &lt;string&gt; using namespace std;class MusicAlbum { public:MusicAlbum(const string maArtist = “”,               const string maTitle = “”,               const int maYear = 0);~MusicAlbum();MusicAlbum(const MusicAlbum &amp;maToCopy);    void operator=(const MusicAlbum &amp;right);    string getMusicAlbumArtist();    string getMusicAlbumTitle();    int getMusicAlbumYear();private:string artist;    string title;    int year;};#endif</td>

  </tr>

 </tbody>

</table>

should be coded in a file called SimpleMusicAlbum.h and its implementation should be coded in a file called SimpleMusicAlbum.cpp.




<ul>

 <li>The MusicAlbum class should have the data members Artist, Title, and Year. You should implement get functions for these data members since they will be used to test your program.</li>

 <li>You should also implement a default constructor that initializes the Artist, Title, and Year data members. Additionally, you should implement your own destructor and copy constructor, and overload the assignment operator. Although you may use the default ones for some of these member functions, you are advised to implement them (although some may have no statements) in Part A so that it will be easier for you to extend them in Part B.</li>

 <li>Do not delete or modify any part of the given data members or member functions. However, you may define additional data members and member functions, if necessary.</li>

</ul>




<ol start="2">

 <li>Below is the required part of the music album collection (MAC) class that you will code in Part A of this assignment. The name of the class should be MAC; the interface for the class:</li>

</ol>

<table width="548">

 <tbody>

  <tr>

   <td width="548">#ifndef __SIMPLE_MAC_H#define __SIMPLE_MAC_H #include &lt;string&gt; using namespace std;#include “SimpleMusicAlbum.h”class MAC{ public:    MAC();~MAC();MAC(const MAC &amp;macToCopy);    void operator=(const MAC &amp;right); bool addMusicAlbum(const string maArtist,                        const string maTitle,                       const int maYear);    bool removeMusicAlbum(const string maArtist,                           const string maTitle);    int getMusicAlbums(MusicAlbum *&amp;allMusicAlbums);private:MusicAlbum *musicAlbums;    int noOfMusicAlbums; };#endif</td>

  </tr>

 </tbody>

</table>

should be coded in a file called SimpleMAC.h and its implementation should be coded in a file called SimpleMAC.cpp.




<ul>

 <li>Implement the default constructor, which creates an empty album music collection. Also overload the assignment operator and implement the destructor and copy constructor.</li>

 <li>Implement the add and remove music album functions whose details are given below:</li>

</ul>

<strong> </strong>

<strong>Add a music album: </strong>This function adds a music album to the collection. The artist<strong>, </strong>the title and the year are specified as parameters. In this collection, the pair of artist and title are unique (however, there can be multiple albums of the same artist and multiple albums with the same title). Thus, if the user attempts to add a music album with an already existing artist and title, do not add the music album and return false. Do not display any warning messages. Otherwise, if the album does not exist in the collection, add it to the collection and return true.

<strong>Remove a music album: </strong>This function removes a music album from the collection. The artist and the title are specified as parameters. If the given album exists in the collection, remove it from the collection and return true. Otherwise, if there is no album with the given artist and title, do not perform any action and return false. Likewise, do not display any warning messages.

<ul>

 <li>Implement the get function for music albums. The getMusicAlbums function should return the number of the music albums in the collection using the return value and the music albums in the collection by a pass-by-reference parameter called allMusicAlbums. Do not forget to put a deep copy of the musicAlbums to the pass-by-reference parameter; otherwise, you may encounter run-time errors.</li>

 <li>Do not delete or modify any part of the given data members or member functions. However, you may define additional functions and data members, if necessary.</li>

</ul>




<ol start="3">

 <li>To test Part A, you should code your own main function in a separate file. Do not forget to test your code for different cases. However, do not submit any file containing the main function; otherwise, you may lose a considerable number of points. We will code our own driver to grade Part A of your assignment. In doing that, we will use the get functions of the MusicAlbum and MAC Thus, do not forget to implement the get functions of these two classes.</li>

</ol>




Below is an example of the test code and its output. In this example code, there is a global function called displayAllMusicAlbums. We will use it to display the music albums in the collection and to understand whether you add/remove music albums correctly. If you want, you may use this global function for your tests as well. Notice that the last two lines of this global function are to deallocate the allMusicAlbums array. Do not remove these two lines if you get any run-time errors while using the function. If you have such run-time errors, most probably, you made an error in implementing either the getMusicAlbums function or one or more of the destructor, copy constructor, and overloaded assignment operator.

<table width="540">

 <tbody>

  <tr>

   <td colspan="2" width="540">#include &lt;iostream&gt; using namespace std;#include “SimpleMusicAlbum.h”#include “SimpleMAC.h” void displayAllMusicAlbums(MAC mac){    MusicAlbum *allMusicAlbums;    int noOfMusicAlbums = mac.getMusicAlbums(allMusicAlbums); cout &lt;&lt;“No of music albums: “&lt;&lt; noOfMusicAlbums &lt;&lt; endl;    for (int i = 0; i &lt; noOfMusicAlbums; i++){        cout &lt;&lt; allMusicAlbums[i].getMusicAlbumArtist() &lt;&lt;“, ”             &lt;&lt; allMusicAlbums[i].getMusicAlbumTitle() &lt;&lt;” (”&lt;&lt; allMusicAlbums[i].getMusicAlbumYear() &lt;&lt;“)”&lt;&lt; endl;}     if (allMusicAlbums != NULL)       delete [] allMusicAlbums; }</td>

   <td width="4"> </td>

  </tr>

  <tr>

   <td width="4"> </td>

   <td colspan="2" width="540">int main(){MAC m; m.addMusicAlbum(“John Coltrane”, “My Favorite Things”,                    1961);    if (m.addMusicAlbum(“John Coltrane”, “A Love Supreme”,1965))cout &lt;&lt; “Successful insertion of John Coltrane, ”&lt;&lt; “A Love Supreme (1965)” &lt;&lt; endl;    else       cout &lt;&lt; “Unsuccessful insertion of John Coltrane, ”&lt;&lt; “A Love Supreme (1965)” &lt;&lt; endl;m.addMusicAlbum(“Jethro Tull”, “Thick As A Brick”,1972);m.addMusicAlbum(“Mike Oldfield”, “Tubular Bells”,1973);m.addMusicAlbum(“Pink Floyd”, “The Dark Side of the Moon”,                    1973);    displayAllMusicAlbums(m);    if (m.removeMusicAlbum(“John Coltrane”, “Giant Steps”))       cout &lt;&lt; “Successful deletion of John Coltrane, ”&lt;&lt; “Giant Steps” &lt;&lt; endl;    else       cout &lt;&lt; “Unsuccessful deletion of John Coltrane, ”            &lt;&lt; “Giant Steps” &lt;&lt; endl;return 0;}</td>

  </tr>

  <tr>

   <td width="4"></td>

   <td width="532"></td>

   <td width="4"></td>

  </tr>

 </tbody>

</table>




The output should be:

Successful insertion of John Coltrane, A Love Supreme (1965)

No of music albums: 5

John Coltrane, My Favorite Things (1961)

John Coltrane, A Love Supreme (1965)

Jethro Tull, Thick As A Brick (1972)

Mike Oldfield, Tubular Bells (1973)

Pink Floyd, The Dark Side of the Moon (1973)

Unsuccessful deletion of John Coltrane, Giant Steps




<strong>What to submit for Part A? </strong>

You should put your SimpleMusicAlbum.h, SimpleMusicAlbum.cpp, SimpleMAC.h<sub>, </sub>and

SimpleMAC.cpp files into a folder and zip the folder. In this zip file, there should not be any file containing the main function. The name of this zip file needs to be

PartA_secX_Firstname_Lastname_StudentID.zip, where X is your section number. Then you should follow the steps that are explained at the end of this document for the submission of Part A.

<strong> </strong>

<strong>What to be careful about implementation and submission for Part A? </strong>

You need to read the “notes about implementation” and the “notes about submission” parts that are given at the end of this document.

<h1>PART B:</h1>

Now, Part A is to be extended such that each music album has a list of songs. The full functionality of this extended MAC system is to be provided. In order for this to be done, the MusicAlbum class needs to be extended such that it additionally keeps the list of songs contained. The song list of a music album must be kept in a dynamically allocated array of Song objects. Note that the number of songs can be different from one music album to another, but is normally fixed for a particular music album. The details of the classes are given below.




<ol>

 <li>The requirements of the Song class are given below. The name of the class should be Song; its interface:</li>

</ol>

<table width="545">

 <tbody>

  <tr>

   <td width="545">#ifndef __SONG_H#define __SONG_H #include &lt;string&gt; using namespace std; class Song { public:Song(const string sName = “”, const int sMins = 0,         const int sSecs = 0);~Song();Song(const Song &amp;songToCopy);    void operator=(const Song &amp;right);private:string name;    int mins;    int secs;};</td>

  </tr>

 </tbody>

</table>

#endif

should be coded in a file called Song.h and its implementation should be coded in a file called Song.cpp.

<ul>

 <li>The Song class keeps the name of a song and its running length in minutes and seconds. The name should be unique for each music album. That is, a music album cannot have multiple songs with the exact same name but different music albums may have a song with the same name.</li>

 <li>Implement your own default constructor, destructor, and copy constructor, and overload the assignment operator.</li>

 <li>Do not delete or modify any part of the given data members or member functions. However, you may define additional functions and data members, if necessary.</li>

</ul>





































<ol start="2">

 <li>The requirements of the MusicAlbum class are given below. The name of the class should be MusicAlbum. This time, the interface for the class:</li>

</ol>

<table width="545">

 <tbody>

  <tr>

   <td width="545">#ifndef __MUSIC_ALBUM_H#define __MUSIC_ALBUM_H #include &lt;string&gt; using namespace std;#include “Song.h”class MusicAlbum { public:MusicAlbum(const string maArtist = “”,               const string maTitle = “”,               const int maYear = 0);~MusicAlbum();MusicAlbum(const MusicAlbum &amp;maToCopy);    void operator=(const MusicAlbum &amp;right);    string getMusicAlbumArtist();    string getMusicAlbumTitle();    int getMusicAlbumYear();    void calculateMusicAlbumLength(int &amp;minutes, int &amp;seconds);private:string artist;    string title;    int year;    Song *songs;    int noSongs;};#endif</td>

  </tr>

 </tbody>

</table>

should be coded in a file called MusicAlbum.h and its implementation should be coded in a file called MusicAlbum.cpp.




<ul>

 <li>The MusicAlbum class is similar to the one given in Part A. However, now it should keep a dynamic array of Song objects as well. Similar to Part A, you should implement your own default constructor, destructor and copy constructor, and do not forget to overload the assignment operator. Also, you should make sure to implement get functions for the Artist, Title and Year data members since they will be used to test your program.</li>

 <li>Your class should have a public member function called calculateMusicAlbumLength which will be used for testing. This function should calculate the running length of the music album upon which it is invoked by summing up the lengths of its songs in minutes and seconds. The running length of the music album should be returned through pass-by-reference parameters called minutes and seconds. Note that in implementing this function, you should use the fact that 1 minute is 60 seconds.</li>

 <li>Do not delete or modify any part of the given data members or member functions. However, you may define additional functions and data members, if necessary.</li>

</ul>




<ol start="3">

 <li>Below is the required part of the MAC class that you will code in Part B of this assignment. The name of the class should be MAC; the interface for the class:</li>

</ol>

<table width="548">

 <tbody>

  <tr>

   <td width="548">#ifndef __MAC_H#define __MAC_H #include &lt;string&gt; using namespace std;#include “MusicAlbum.h”class MAC{ public:    MAC();~MAC();MAC(const MAC &amp;macToCopy);    void operator=(const MAC &amp;right);    bool addMusicAlbum(const string maArtist,                        const string maTitle,                       const int maYear);    bool removeMusicAlbum(const string maArtist,                           const string maTitle);    int getMusicAlbums(MusicAlbum *&amp;allMusicAlbums);    bool addSong(const string maArtist, const string maTitle,                 const string sName, const int sMins,                 const int sSecs);    bool removeSongs(const string maArtist,                     const string maTitle);    void calculateAvgMusicAlbumLength(int &amp;minutes,                                      int &amp;seconds);private:MusicAlbum *musicAlbums;    int noOfMusicAlbums; };#endif</td>

  </tr>

 </tbody>

</table>

should be coded in a file called MAC.h and its implementation should be coded in a file called MAC.cpp.




<ul>

 <li>The MAC class is similar to the one given in Part A. However, now it should also keep the list of songs for each music album. Similar to Part A, you should implement your own default constructor, destructor and copy constructor, and overload the assignment operator. Also you should make sure to implement the getMusicAlbums function, as explained before.</li>

 <li>Implement the following functions that your extended system should support.</li>

</ul>

<strong> </strong>

<strong>Add a music album: </strong>This function adds a music album to the collection. The artist<strong>, </strong>the title and the year are specified as parameters. In this function, the song list is not specified; the song(s) will be added later. In the music album collection, the pair of artist and title are unique (however, there can be multiple albums of the same artist and multiple albums with the same title). Thus, if the user attempts to add a music album with an already existing artist and title, do not add the music album and return false. Do not display any warning messages. Otherwise, if the album does not exist in the collection, add it to the collection and return true. This function is similar to what you will have implemented in Part A. But, in Part B, you should also create an empty song list for the music album when you add it to the collection.

<strong>Remove a music album: </strong>This function removes a music album from the collection. The artist and the title are specified as parameters. If the given album exists in the collection, remove it from the collection and return true. Otherwise, if there is no album with the given artist and title, do not perform any action and return false. Likewise, do not display any warning messages. Note that this function should also clear the song list of the specified music album. This function is similar to what you will have implemented in Part A. But now, for Part B, you should also remove the song list when you remove the music album from the collection.

<strong> </strong>

<strong>Add a song to the music album: </strong>This function adds a song to the song list of a music album in the collection. The artist<strong>, </strong>the title and the year together with the name and the running length of the song in minutes and seconds are specified as parameters. In this function, you should take care of the following issues: o If the specified music album does not exist in the collection, do not perform any action and return false. Do not display any warning messages. o All song names are unique in a music album. Thus, if the user attempts to add a song with an existing name for the specified music album, do not perform any action and return false. Do not display any warning messages. (However, different music albums may have a song with the same name.)

o Otherwise, add the song to the song list of the specified music album and return true.

<strong> </strong>

<strong>Remove song list from the music album: </strong>This function clears the song list of a music album. The artist and the title are given as parameters. If there is no music album with the specified artist and title, or if there are no songs in the song list, do not perform any action and return false. Do not display any warning messages. Otherwise, clear the song list of the specified music album and return true.

<strong> </strong>

<strong>Calculate the average running length of music albums in the collection: </strong>This function calculates the average running length of all music albums in the collection in minutes and seconds and returns the result through pass-by-reference parameters called minutes and seconds. Note that in implementing this function you should resort to the calculateMusicAlbumLength function of the MusicAlbum class and use the fact that 1 minute is 60 seconds. If there are no music albums in the collection, or all music albums have empty song lists, this function should return 0 minutes and 0 seconds.

<strong> </strong>

<ul>

 <li>Do not delete or modify any part of the given data members or member functions. However, you may define additional functions and data members, if necessary.</li>

</ul>




<ol start="4">

 <li>To test Part B, you should code your own main function in a separate file. Do not forget to test your code for different cases. However, do not submit any file containing the main function; otherwise, you may lose a considerable number of points. We will code our own driver to grade Part B of your assignment. In doing that, we will use the get functions of the MusicAlbum and MAC Thus, do not forget to implement the get functions of these two classes.</li>

</ol>




Below is an example of the test code and its output. In this example code, there are two global functions called displayAllMusicAlbums and displayStatistics. The former is the same as the one implemented for Part A. The purpose of the latter is to obtain some statistics about music albums of artists. We will use these functions to understand whether you add/remove music

<table width="540">

 <tbody>

  <tr>

   <td width="540">#include &lt;iostream&gt;#include “MusicAlbum.h” #include “MAC.h” using namespace std; void displayAllMusicAlbums(MAC mac){    MusicAlbum *allMusicAlbums;    int noOfMusicAlbums = mac.getMusicAlbums(allMusicAlbums);cout &lt;&lt;“No of music albums: “&lt;&lt; noOfMusicAlbums &lt;&lt; endl;    for (int i = 0; i &lt; noOfMusicAlbums; i++){        cout &lt;&lt; allMusicAlbums[i].getMusicAlbumArtist() &lt;&lt;“, ”             &lt;&lt; allMusicAlbums[i].getMusicAlbumTitle() &lt;&lt;” (”&lt;&lt; allMusicAlbums[i].getMusicAlbumYear() &lt;&lt;“)”&lt;&lt; endl;}if (allMusicAlbums != NULL)       delete [] allMusicAlbums;}  void displayStatistics(MAC mac){    MusicAlbum *allMusicAlbums;    int noOfMusicAlbums = mac.getMusicAlbums(allMusicAlbums);    int count[8] = {0};    int mins, secs;for (int i = 0; i &lt; noOfMusicAlbums; i++) {        allMusicAlbums[i].calculateMusicAlbumLength(mins,                                                    secs);        if (mins &lt; 70)           count[mins/10]++;        elsecount[7]++;}for (int i = 0; i &lt; 7; i++)        if (count[i] &gt; 0)           cout &lt;&lt;“Number of albums with running time in [ ”&lt;&lt; i*10 &lt;&lt; “,” &lt;&lt; (i+1)*10 &lt;&lt; “) minutes: ”&lt;&lt; count[i] &lt;&lt; endl;    if (count[7] &gt; 0)       cout &lt;&lt; “Number of albums with running time &gt;= 70 ”&lt;&lt; “minutes: ” &lt;&lt; count[7] &lt;&lt; endl;    mac.calculateAvgMusicAlbumLength(mins, secs);    cout &lt;&lt; “Average album running time: ” &lt;&lt; mins&lt;&lt; ” minutes, ” &lt;&lt; secs &lt;&lt; ” seconds” &lt;&lt; endl; if (allMusicAlbums != NULL)       delete [] allMusicAlbums; }</td>

  </tr>

  <tr>

   <td width="540">int main(){MAC m; m.addMusicAlbum(“John Coltrane”, “My Favorite Things”,1961);m.addSong(“John Coltrane”, “My Favorite Things”,“My Favorite Things”, 13, 44);m.addSong(“John Coltrane”, “My Favorite Things”,“Ever’y Time We Say Goodbye”, 5, 43);m.addSong(“John Coltrane”, “My Favorite Things”,“Summertime”, 11, 36);m.addSong(“John Coltrane”, “My Favorite Things”,“But Not For Me”, 9, 35); m.addMusicAlbum(“John Coltrane”, “A Love Supreme”,1965);m.addSong(“John Coltrane”, “A Love Supreme”,“Acknowledgement”, 7, 48);m.addSong(“John Coltrane”, “A Love Supreme”,“Resolution”, 7, 25);m.addSong(“John Coltrane”, “A Love Supreme”,“Pursuance”, 10, 46);m.addSong(“John Coltrane”, “A Love Supreme”,              “Psalm”, 7, 05); m.addMusicAlbum(“Jethro Tull”, “Thick As A Brick”,1972);m.addSong(“Jethro Tull”, “Thick As A Brick”,              “Thick As A Brick, Part 1”, 22, 45);m.addSong(“Jethro Tull”, “Thick As A Brick”,“Thick As A Brick, Part 2”, 21, 05); m.addMusicAlbum(“Mike Oldfield”, “Tubular Bells”,1973);m.addSong(“Mike Oldfield”, “Tubular Bells”,“Part One”, 25, 00);m.addSong(“Mike Oldfield”, “Tubular Bells”,              “Part Two”, 23, 50); m.removeMusicAlbum(“John Coltrane”, “My Favorite Things”);displayAllMusicAlbums(m);    displayStatistics(m);return 0;}</td>

  </tr>

 </tbody>

</table>

albums and song lists correctly. If you want, you may use these global functions for your tests as well. Again the last two lines are included to deallocate the allMusicAlbums array. Do not remove these lines if you get any run-time errors while using these functions. If you have such runtime errors, most probably, you made an error in implementing either the getMusicAlbumsfunction or one or more of the destructor, copy constructor, and overloaded assignment operator.







The output should be:

No of music albums: 3

John Coltrane, A Love Supreme (1965)

Jethro Tull, Thick As A Brick (1972)

Mike Oldfield, Tubular Bells (1973)

Number of albums with running time in [30,40) minutes: 1

Number of albums with running time in [40,50) minutes: 2

Average album running time: 41 minutes, 54 seconds

<strong> </strong>

<strong>What to submit for Part B? </strong>

You should put your MusicAlbum.h, MusicAlbum.cpp, Song.h, Song.cpp, MAC.h<sub>, </sub>and

MAC.cpp files into a folder and zip the folder. In this zip file, there should not be any file containing the main function. The name of this zip file should be

PartB_secX_Firstname_Lastname_StudentID.zip where X is your section number. Then you should follow the steps explained at the end of this document for the submission of Part B.




<strong>What to be careful about implementation and submission for Part B? </strong>

You need to read the “notes about implementation” and “notes about submission” parts that are given just below.




<strong>NOTES ABOUT IMPLEMENTATION (for both Part A and Part B): </strong>

<ol>

 <li>You must use dynamically allocated arrays. You will receive no points if you use fixed-sized arrays, linked-lists or any other data structures such as vector/array from the standard library.</li>

 <li>You are not allowed to use any global variables or any global functions when implementing the classes. However, you may use global functions to test your program, but should not submit them.</li>

</ol>

Your code must not have any memory leaks. You will lose points if your code has memory leaks even though it produces correct output. To detect memory leaks, you may