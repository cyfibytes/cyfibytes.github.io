# Hide Secret Data Using Steganography
Your communications are being monitored by employers, third party services, and prying eyes. As privacy continues to be obstructed and impeded upon, users will find alternative methods of communicating to avoid being monitored.

To hide the existence of data from a third party we can use a covert communication art known as steganography. Steganography is the practice of concealing data by embedding it within other data, such as audio, video, or an image file. The difference between steganography and encryption is that only the sender and recipient know that there is hidden data.

In this tutorial you will learn how to conceal data in an image, and then learn how to extract that same hidden data from the image. 

## Prerequisites
For this tutorial we will be using the open-source program [Steghide](https://github.com/StefanoDeVuono/steghide).

Install Steghide from the terminal in Linux.
```shell
sudo apt-get install steghide
```

Use the `--help` flag to view options available for Steghide.
```shell
steghide --help
```

### Basic Usage
Steghide requires a command that tells the tool what action to perform.

```
steghide {embed/extract/info} [arguments]
```

| Action      | Description                              |
|:------------|:-----------------------------------------|
| **embed**   | Perform an embed.                        |
| **extract** | Perform an extraction.                   |
| **info**    | View information about a file received.  |

| Argument | Description |
|:---------|:----------- |
| **-ef**  | Specifies the path of the file that you want to hide. You can embed any kind of file inside of the cover file, including Python scripts or shell files. |
| **-cf**  | The file that the data is embedded into. This is restricted to BMP, JPEG, WAV, and AU files. |
| **-sf**  | Optional argument that specifies the output file. If this is omitted, the original cover file will be overwritten by your new steganographic file. |
| **-z**   | Specifies the compression level, between 1 and 9. If you prefer not to compress your file, use the argument `-Z` instead. |
| **-e**   | Specifies the type of encryption. Steghide supports a multitude of encryption schemes, and if this argument is omitted by default, Steghide will use 128-bit AES encryption. If you prefer not use encryption, simply type -e none. |

We are going to use the image below to conceal a message. Save the image to your machine.

![car](car.jpg)

Create a text file with the following message:
```
echo "The quieter you become, the more you can hear." > secret.txt
```

## Conceal Secret Message
Now that we have an image to conceal our message we can embed the file within the image.

```
steghide embed -ef <PATH/TO/EMBED/FILE> -cf <PATH/TO/COVER/FILE>
```

This command will embed the file `secret.txt` in the cover file `car.jpg`.
```shell
steghide embed -ef secret.txt -cf car.jpg
```

You will be prompted to enter a password to secure the encoded file. Try using the passphrase `Pa$$w0rd`.
```
Enter a passphrase:
Re-Enter passphrase:
```

## Extract Secret Message

```
steghide extract -sf </PATH/TO/FILE> -p [password] -xf <PATH/TO/NEW/FILE>
```

```shell
steghide extract -sf cat.jpg -p Pa$$w0rd -xf message.txt
```

Enter the passphrase you used to secure the encoded file.
```
Enter a passphrase: 
Re-Enter passphrase:
```

## Next Steps
Practice communicating using steganography by sharing this tutorial with someone. Take your covert communication skills further by sharing the passphrase to steganographic files over a secure, offline communication channel.
