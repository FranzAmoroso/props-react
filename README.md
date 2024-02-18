# props

Le **props** sono un meccanismo fondamentale in React per passare dati da un **componente padre** a un **componente figlio**. Consentono di rendere i componenti React dinamici e riutilizzabili, consentendo loro di accettare input esterni e renderizzare output basati su tali input.

### Passaggio dei dati:


Le props vengono utilizzate per passare dati da un componente genitore a un componente figlio durante la creazione del componente figlio. Utilizzando **props**, è possibile creare componenti React altamente riutilizzabili e configurabili che possono essere utilizzati in diverse parti dell'applicazione.


    <Card
    title="California"
    description="Soleggiata, spiagge, Hollywood, tecnologia, multiculturalità, surf, parchi nazionali, Silicon Valley, Los Angeles, San Francisco."
    imgURL="https://images.pexels.com/photos/3881036/pexels-photo-3881036.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
    ></Card>

Nel componente genitore `App.jsx,` le props vengono utilizzate per **passare dati** ai componenti figlio Card. Ad esempio, le props title, description, e imgURL contengono dati specifici relativi a ciascuna carta e vengono passate come argomenti ai componenti Card.

### Accesso alle Props nel Componente Figlio:

Le props sono accessibili come oggetto JavaScript nel componente figlio e possono essere lette per ottenere i dati passati dal componente genitore. Nel componente figlio, le props sono considerate "solo lettura".

    function Card({ title, imgURL }) {
    // Accesso alle props
    }

Nel componente figlio Card.jsx, le props vengono accessate utilizzando la sintassi {} e l'oggetto props. Ad esempio, props.title e props.imgURL vengono utilizzati per estrarre i dati relativi al titolo e all'URL dell'immagine passati dal componente genitore.

### Utilizzo delle Props per Personalizzare i Componenti:

Le props consentono di personalizzare il comportamento e l'aspetto dei componenti in base ai dati passati. Ad esempio, è possibile passare un colore o un testo diverso a un componente per personalizzarne l'aspetto o il contenuto.


    <h2 className="text-2xl">{title}</h2>
    <img src={imgURL} alt="" className="h-[300px]" />

Nel componente `Card.jsx`, le props estratte vengono utilizzate per personalizzare l'aspetto delle carte. Ad esempio, il titolo viene utilizzato all'interno di un tag h2, mentre l'URL dell'immagine viene utilizzato come attributo src per il tag img.

### Accesso ai Children nel Componente Figlio:

Oltre alle **props standard** come title e description, è possibile passare componenti React aggiuntivi al componente figlio utilizzando la **prop speciale children**. Questo permette di includere elementi JSX arbitrari all'interno del componente figlio e di renderizzarli dove necessario.

    function Card({ children }) {
    // Accesso ai children
    return <>{children}</>;
    }

Nel componente figlio `Card.jsx`, i **children** possono essere acceduti attraverso la **props speciale children**. Questi children possono essere ulteriormente personalizzati e resi parte del rendering del componente figlio.


    <Card>
    <div className="rounded-md bg-gradient-to-br to-sky-950 from-slate-950">
        <img src="https://roma.png" alt="" className="h-[300px]" />
        <div className="flex flex-col p-4">
        <h2 className="text-2xl">Roma</h2>
        <p className="text-gray-500">lorem ispum </p>
        </div>
    </div>
    </Card>

In questo esempio, un blocco di immagine e testo viene passato come children al componente Card. Questi children possono essere resi parte del rendering del componente Card e personalizzati secondo necessità.

### Utilizzo della Proprietà dinamiche come Contenuto Predefinito:

Nel componente Card, la prop speciale `"children"` viene utilizzata come contenuto predefinito nel caso in cui la prop `"description"` **non sia definita**. Questo consente una maggiore flessibilità nell'utilizzo del componente, in quanto consente sia di passare direttamente una descrizione tramite la prop `"description"`, sia di inserire direttamente del contenuto tramite i children.


    <p className="text-gray-500">{description || children}</p>

Nella definizione del paragrafo all'interno del componente Card, viene verificato se la prop `"description"` è definita. Se la prop `"description"` è definita e non è vuota, il suo valore viene utilizzato come contenuto del paragrafo. In caso contrario, viene utilizzato il contenuto passato tramite i children.

