```

import './App.css'
import {useEffect, useState} from "react";

function App() {
    const [pokemon, setPokemon] = useState()

    useEffect(() => {
        async function getPokemon() {
            const response = await fetch(
                `http://localhost:8000/pokemon`,
                {
                    method: "GET"
                }
            )
            const data = await response.json()
            console.log(data.data.name)

            setPokemon(data.data)
        }

        getPokemon()
    }, []);

  return (
    <>
        <div>
            {pokemon ?
                <ul>
                    <h1>Poke id: {pokemon.id}</h1>
                    <h2>Poke name: {pokemon.name}</h2>
                </ul>
                : <h1>No data</h1>
            }
        </div>
    </>
  )
}

export default App


```