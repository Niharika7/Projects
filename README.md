# Projects
from django.contrib.auth.models import Permission, User
from django.db import models


class Album(models.Model):
    user = models.ForeignKey(User, default=1)
    artist = models.CharField(max_length=250)
    album_title = models.CharField(max_length=500)
    genre = models.CharField(max_length=100)
    album_logo = models.FileField()
    is_favorite = models.BooleanField(default=False)

    def __str__(self):
        return self.album_title + ' - ' + self.artist


class Song(models.Model):
    album = models.ForeignKey(Album, on_delete=models.CASCADE)
    song_title = models.CharField(max_length=250)
    audio_file = models.FileField(default='')
    is_favorite = models.BooleanField(default=False)

    def __str__(self):
        return self.song_title

class Artist(models.Model):
    category=models.CharField(max_length=50)
    no_of_albums=models.IntegerField(max_length=50)

class Record_Company(models.Model):
    name=models.CharField(max_length=50)
    address=models.CharField(max_length=50)
    phone=models.IntegerField(max_length=10)

class User(models.Model):
    username=models.CharField(max_length=50)
    email_id=models.CharField(max_length=50)
    password=models.CharField(max_length=50)

