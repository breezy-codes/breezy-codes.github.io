# Creating Form Spam for a Cybersecurity Challenge

As technology and cybersecurity enthusiasts, we often find ourselves in situations where creativity meets a bit of controlled chaos. Recently, I had the opportunity to contribute to a Capture The Flag (CTF) challenge for the Safer Internet Project. Our goal was to create a scenario where participants had to identify a hidden person among a sea of fake form submissions. To achieve this, I had to craft a method for filling out a web form with a barrage of spam submissions.

## The Challenge

Part of the CTF challenge involved this form on this fake website where people would fill it out and send their “resume”. Among the mass of submissions, one submission held the key to the next stage of the competition. The challenge was to distinguish the genuine submission from the impostors. To make the challenge more engaging, we needed to flood the form with a multitude of fake submissions, making it challenging to identify the authentic one.

## The Journey

At the outset, I wasn't entirely sure how to approach this task. I had just completed a room on TryHackMe a few days prior where I had to write a python script to target a site and brute force my way to find the username and password to gain access. I thought I could potentially use a similar construct to mass fill out this form. Here's how I tackled it:

1. **Identifying the Form:** I began by inspecting the website's HTML structure to locate the form and extract its details. This included finding the form's endpoint URL and identifying the form input fields.
2. **Automating Data Generation:** To automate the process of generating fake form submissions, I turned to the "Faker" library in Python. This versatile library allowed me to create fake names and email addresses, which were essential for crafting convincing submissions.
3. **Creating the Loop:** With the necessary data generation tools in place, I wrote a Python script to loop through a set number of iterations, each simulating a form submission. The loop allowed me to generate unique names and emails for each submission.
4. **Delay and Caution:** To avoid overwhelming the target site or triggering any security measures, I introduced a delay of 5 seconds between submissions. This cautious approach ensured a controlled and inconspicuous spamming process.
5. **Unique Identifiers:** In the form data, I included a unique identifier for each submission, such as "test user 1," "test user 2," and so on. This made it easier to track the submissions and identify the key submission later.

## The Code

Below is the Python code used to automate the form spamming process:

```py
import requests
from faker import Faker
import time

fake = Faker()

url = 'https://formbold.com/s/94ERW'

resume_file = ('resume.pdf', open('resume.pdf', 'rb'))

num_submissions = 100
submission_delay = 5

for i in range(1, num_submissions + 1):
    username = f'test user {i}'

    form_data = {
        'text_input_F94A5B92-B932-4732-A178-B7D86B205264': username,
        'email_input_FA91759C-7B7B-4D72-97BD-39D7F1661C28': fake.email(),
    }

    response = requests.post(url, data=form_data, files={'file_attachment_EF6C31A2-6562-4173-AA90-4182F12FF1D5': resume_file})

    if response.status_code == 200:
        print(f"Form submitted successfully for {username}.")
    else:
        print(f"Form submission failed for {username} with status code: {response.status_code}")

    time.sleep(submission_delay)
```

## Conclusion

In the world of cybersecurity challenges, creativity knows no bounds. Crafting a controlled chaos scenario for a CTF challenge required some clever thinking and technical skills. While it might seem counterintuitive to spam a form, it served a purpose by adding an extra layer of intrigue to the competition. The combination of web form manipulation and Python automation allowed me to take on a new challenge and find ways to use my new skills to help in this CTF build. In the end, it's about pushing the boundaries of what's possible and having fun while doing it.
