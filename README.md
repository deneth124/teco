# teco
import random
import openai

# If you want to use OpenAI API to generate invention ideas, you need an API key.
openai.api_key = 'YOUR_API_KEY'

# Function to generate ideas using OpenAI's GPT model
def generate_invention_idea_with_gpt(prompt="Generate an invention idea:"):
    try:
        response = openai.Completion.create(
            engine="text-davinci-003",  # GPT model to use
            prompt=prompt,
            max_tokens=100,  # Limit the response length
            temperature=0.7  # Controls randomness
        )
        idea = response.choices[0].text.strip()
        return idea
    except Exception as e:
        return f"Error generating idea: {str(e)}"

# Function to get a random invention idea from a predefined list
def generate_random_invention():
    ideas = [
        "A device that automatically organizes your bookshelf based on book genre.",
        "A smart mirror that provides real-time health information as you get ready.",
        "A self-cleaning water bottle with a built-in filtration system.",
        "A portable solar-powered phone charger that fits in your wallet.",
        "A robot vacuum that can be controlled by voice commands through your smartphone.",
        "A wearable device that helps you practice mindfulness and reduce stress.",
        "A smart refrigerator that tracks expiration dates and suggests recipes.",
        "An app that helps you find local sustainable and eco-friendly products.",
        "A gadget that turns any flat surface into a touch screen interface.",
        "An intelligent waste bin that sorts recyclables and trash automatically."
    ]
    return random.choice(ideas)

# Main function to interact with the user
def main():
    print("Welcome to the Invention Idea Generator!")
    print("Choose an option:")
    print("1. Get a random invention idea")
    print("2. Get an invention idea from GPT")

    choice = input("Enter your choice (1 or 2): ")

    if choice == "1":
        print("\nYour invention idea is:")
        print(generate_random_invention())
    elif choice == "2":
        print("\nFetching an invention idea from GPT...")
        prompt = input("Enter a prompt for the invention idea: ")
        print("\nYour invention idea is:")
        print(generate_invention_idea_with_gpt(prompt))
    else:
        print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
