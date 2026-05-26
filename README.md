# Tugas-program-linked-list
Daftar muski menggunakan program linked list
# Program Linked List - Daftar Putar Musik

class Lagu:
    def __init__(self, judul):
        self.judul = judul
        self.next = None


class Playlist:
    def __init__(self):
        self.head = None

    # Menambah lagu ke akhir playlist
    def tambah_lagu(self, judul):
        lagu_baru = Lagu(judul)

        if self.head is None:
            self.head = lagu_baru
        else:
            current = self.head
            while current.next:
                current = current.next
            current.next = lagu_baru

    # Menghapus lagu berdasarkan judul
    def hapus_lagu(self, judul):
        current = self.head

        if current and current.judul == judul:
            self.head = current.next
            return

        prev = None
        while current and current.judul != judul:
            prev = current
            current = current.next

        if current:
            prev.next = current.next

    # Menampilkan playlist
    def tampilkan_playlist(self):
        if self.head is None:
            print("Playlist kosong")
        else:
            current = self.head
            print("Daftar Putar Musik:")
            while current:
                print("-", current.judul)
                current = current.next


# Program utama
playlist = Playlist()

playlist.tambah_lagu("Hati-Hati di Jalan")
playlist.tambah_lagu("Komang")
playlist.tambah_lagu("Sial")

playlist.tampilkan_playlist()

print("\nMenghapus lagu: Komang\n")
playlist.hapus_lagu("Komang")

playlist.tampilkan_playlist()
