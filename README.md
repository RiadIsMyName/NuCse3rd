# NuCse3rd.Github.io
import requests

def upload_pdf(pdf_path, filename):
    """Uploads a PDF file to the GitHub website.

    Args:
        pdf_path (str): The path to the PDF file to upload.
        filename (str): The filename to use for the uploaded file.

    Returns:
        str: The URL of the uploaded file.
    """

    url = "https://api.github.com/repos/<username>/<repo>/contents/<filename>"
    headers = {"Authorization": "bearer <token>"}
    with open(pdf_path, "rb") as f:
        data = f.read()

    response = requests.post(url, headers=headers, data=data)
    if response.status_code == 200:
        return response.json()["url"]
    else:
        raise Exception("Failed to upload PDF file.")


def main():
    pdf_path = "path/to/pdf/file.pdf"
    filename = "my-pdf-file.pdf"
    url = upload_pdf(pdf_path, filename)
    print(url)


if __name__ == "__main__":
    main()

