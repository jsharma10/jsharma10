import requests
from bs4 import BeautifulSoup

def scrape_linkedin_profile(url):
   
    response = requests.get(url)
    
    
    soup = BeautifulSoup(response.content, 'html.parser')
    

    name = soup.select_one('.pv-top-card--list .pv-top-card--list-item').get_text().strip()
    headline = soup.select_one('.pv-top-card--list .pv-top-card--list-bullet').get_text().strip()

    return {'name': name, 'headline': headline}

if __name__ == '__main__':
    linkedin_url = 'https://www.linkedin.com/in/exampleprofile'
    profile_data = scrape_linkedin_profile(linkedin_url)
    print(profile_data)
