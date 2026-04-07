#include <iostream>
#include <vector>
using namespace std;

class Song {
public:
    string title;
    string artist;

    Song(string t, string a) {
        title = t;
        artist = a;
    }
};

vector<Song> playlist;

// Add Song
void addSong() {
    string title, artist;
    cout << "Enter song title: ";
    cin.ignore();
    getline(cin, title);
    cout << "Enter artist name: ";
    getline(cin, artist);

    playlist.push_back(Song(title, artist));
    cout << "Song added successfully!\n";
}

// Display Playlist
void displayPlaylist() {
    if (playlist.empty()) {
        cout << "Playlist is empty!\n";
        return;
    }

    cout << "\n--- Playlist ---\n";
    for (int i = 0; i < playlist.size(); i++) {
        cout << i + 1 << ". " << playlist[i].title 
             << " - " << playlist[i].artist << endl;
    }
}

// Delete Song
void deleteSong() {
    int index;
    displayPlaylist();
    cout << "Enter song number to delete: ";
    cin >> index;

    if (index > 0 && index <= playlist.size()) {
        playlist.erase(playlist.begin() + index - 1);
        cout << "Song deleted successfully!\n";
    } else {
        cout << "Invalid selection!\n";
    }
}

// Search Song
void searchSong() {
    string title;
    cin.ignore();
    cout << "Enter song title to search: ";
    getline(cin, title);

    for (auto &song : playlist) {
        if (song.title == title) {
            cout << "Found: " << song.title 
                 << " - " << song.artist << endl;
            return;
        }
    }
    cout << "Song not found!\n";
}

int main() {
    int choice;

    do {
        cout << "\n--- Music Playlist Manager ---\n";
        cout << "1. Add Song\n";
        cout << "2. Display Playlist\n";
        cout << "3. Delete Song\n";
        cout << "4. Search Song\n";
        cout << "5. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1: addSong(); break;
            case 2: displayPlaylist(); break;
            case 3: deleteSong(); break;
            case 4: searchSong(); break;
            case 5: cout << "Exiting...\n"; break;
            default: cout << "Invalid choice!\n";
        }
    } while (choice != 5);

    return 0;
}

# MUSIC-PLAYLIST-MANAGER
The Music Playlist Manager is a menu-driven application developed using C++ that allows users to manage a collection of songs efficiently. It uses a vector (dynamic array) to store song details such as title, artist, and duration.
