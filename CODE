from PIL import Image

def encrypt_image(image_path, key):
    try:
        # Open the image
        img = Image.open(image_path)

        # Get image size and pixel data
        width, height = img.size
        pixels = img.load()

        # Validate key: Key should be an integer between 0 and 255 (8-bit)
        if not isinstance(key, int) or key < 0 or key > 255:
            raise ValueError("Key must be an integer between 0 and 255")

        # Encrypt each pixel using XOR with the key
        for i in range(width):
            for j in range(height):
                r, g, b = pixels[i, j]
                r = r ^ key
                g = g ^ key
                b = b ^ key
                pixels[i, j] = (r, g, b)

        # Save the encrypted image
        encrypted_image_path = 'encrypted_image.png'
        img.save(encrypted_image_path)
        return encrypted_image_path

    except Exception as e:
        print("Error encrypting image: " + str(e))
        return None

def decrypt_image(encrypted_image_path, key):
    try:
        # Open the encrypted image
        img = Image.open(encrypted_image_path)

        # Get image size and pixel data
        width, height = img.size
        pixels = img.load()

        # Validate key: Key should be an integer between 0 and 255 (8-bit)
        if not isinstance(key, int) or key < 0 or key > 255:
            raise ValueError("Key must be an integer between 0 and 255")

        # Decrypt each pixel using XOR with the key
        for i in range(width):
            for j in range(height):
                r, g, b = pixels[i, j]
                r = r ^ key
                g = g ^ key
                b = b ^ key
                pixels[i, j] = (r, g, b)

        # Save the decrypted image
        decrypted_image_path = 'decrypted_image.png'
        img.save(decrypted_image_path)
        return decrypted_image_path

    except Exception as e:
        print("Error decrypting image: " + str(e))
        return None

def main():
    try:
        # Prompt user for image path and key
        image_path = input("Enter the path to the image file: ")
        key = int(input("Enter an integer key between 0 and 255: "))

        # Encrypt the image
        encrypted_image_path = encrypt_image(image_path, key)
        if encrypted_image_path:
            print("Image encrypted successfully. Encrypted image saved as: " + encrypted_image_path)

            # Prompt for decryption
            decrypt_choice = input("Do you want to decrypt the image? (yes/no): ").strip().lower()
            if decrypt_choice == "yes":
                # Prompt user for decryption key
                decrypt_key = int(input("Enter the decryption key (same as encryption key): "))
                if decrypt_key == key:
                    # Decrypt using the same key
                    decrypted_image_path = decrypt_image(encrypted_image_path, key)
                    if decrypted_image_path:
                        print("Image decrypted successfully. Decrypted image saved as: " + decrypted_image_path)
                else:
                    print("Decryption key does not match encryption key. Decryption aborted.")

    except ValueError as ve:
        print("Invalid input: " + str(ve))
    except Exception as e:
        print("Error: " + str(e))

# Call main function directly
main()
