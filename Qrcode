import qrcode

def generate_qr_code(data, filename):
    qr = qrcode.QRCode(
        version=1,
        box_size=10,
        border=5)
    qr.add_data(data)
    qr.make(fit=True)
    img = qr.make_image(fill_color="black", back_color="white")
    img.save(filename)

def main():
    data = input("Enter the data to encode in the QR code: ")
    filename = input("Enter the filename to save the QR code (e.g., qr_code.png): ")
    generate_qr_code(data, filename)
    print(f"QR code saved to {filename}")

if __name__ == "__main__":
    main()
