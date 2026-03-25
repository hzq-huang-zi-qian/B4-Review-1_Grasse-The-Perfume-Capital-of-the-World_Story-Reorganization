<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Progress & Preservation Game</title>
    <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .custom-scrollbar::-webkit-scrollbar { width: 6px; height: 6px; }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: #e2e8f0; border-radius: 10px; }
    </style>
</head>
<body class="bg-slate-100">
    <div id="root"></div>

    <script type="text/babel">
        const { useState, useEffect } = React;

        const initialSections = [
            { id: 'sec1', label: 'Core Concept: Identity', sentences: [
                { id: 's1-1', text: 'Cultural heritage gives us precious glimpses of life in the past and therefore adds to our own sense of identity.', order: 1 },
                { id: 's1-2', text: 'Despite this, our traditional view of progress has often been "out with the old, in with the new."', order: 2 },
                { id: 's1-3', text: "It is necessary that development take place, of course, but this doesn't have to come at the cost of destroying ancient treasures that can never be replaced.", order: 3 },
            ]}
            // ... (其他段落為了精簡先省略，您可以自行貼入之前的內容)
        ];

        const App = () => {
            const [shuffled, setShuffled] = useState([]);
            const [placements, setPlacements] = useState({});

            useEffect(() => {
                setShuffled(initialSections.map(s => ({
                    id: s.id,
                    data: [...s.sentences].sort(() => Math.random() - 0.5)
                })));
            }, []);

            return (
                <div className="p-8">
                    <h1 className="text-2xl font-bold mb-4 text-indigo-600">Progress & Preservation 遊戲已上線！</h1>
                    <div className="bg-white p-6 rounded-xl shadow-lg border border-indigo-100">
                        <p className="text-slate-600 mb-4">如果您看到這個畫面，代表網站已經成功運作了。</p>
                        {/* 這裡會跑出您的遊戲介面 */}
                        <div className="space-y-4">
                            {initialSections[0].sentences.map((s, i) => (
                                <div key={i} className="p-3 border rounded-lg bg-slate-50">
                                    {s.text}
                                </div>
                            ))}
                        </div>
                    </div>
                </div>
            );
        };

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
