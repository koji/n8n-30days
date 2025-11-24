# Day 7 - Pokémon API Integration with Google Gemini

Created an AI-powered Pokémon information assistant that fetches data from PokeAPI and responds to natural language queries.

## Features

- Chat interface for natural language queries about Pokémon
- Google Gemini integration for understanding user requests
- Automatic Japanese to English translation for Pokémon names
- Fetches detailed Pokémon information from PokeAPI
- Formatted responses with key Pokémon details
- Conversation memory for context-aware interactions

## Workflow

![day7-workflow](./workflow.png)

## Example Interaction

1. User asks about a Pokémon (e.g., "Tell me about Pikachu" or "ピカチュウについて教えて").
2. The AI processes the request and fetches data from PokeAPI.
3. System responds with:
   - Pokédex number
   - English name and color
   - Legendary/Mythical status
   - Flavor text in Japanese or English

https://github.com/user-attachments/assets/8e32505e-96f4-4dd9-968f-5c8e2bfe4996

## Requirements

- Google Gemini API key
- Access to PokeAPI (https://pokeapi.co/)

## Workflow JSON

See [Pokemon_API_Workflow.json](./Pokemon_API_Workflow.json) for the workflow configuration.
