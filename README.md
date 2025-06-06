// Fruitopia: HORT-222 Educational Game import React, { useState } from "react"; import { Button } from "@/components/ui/button"; import { Card, CardContent } from "@/components/ui/card";

const levels = [ { title: "Level 1: ज्ञान का बीज", question: "आम की खेती के लिए सबसे उपयुक्त जलवायु कौनसी है?", options: [ "शीतोष्ण जलवायु", "उष्णकटिबंधीय जलवायु", "शुष्क जलवायु", "मरुस्थलीय जलवायु" ], answer: 1 }, { title: "Level 2: बगान का योद्धा", question: "केले का प्रमुख रोग 'पनामा विल्ट' किसके द्वारा होता है?", options: [ "कीट", "फफूंदी", "बैक्टीरिया", "वायरस" ], answer: 1 }, { title: "Level 3: जीवन का रस", question: "फलों को भंडारण से पहले कौनसी प्रक्रिया की जाती है?", options: [ "कटाई", "पैकिंग", "वर्गीकरण और ग्रेडिंग", "परिवहन" ], answer: 2 } ];

export default function FruitopiaGame() { const [level, setLevel] = useState(0); const [score, setScore] = useState(0); const [selected, setSelected] = useState(null);

const current = levels[level];

const handleAnswer = (index) => { setSelected(index); if (index === current.answer) { setScore(score + 10); } setTimeout(() => { setSelected(null); if (level + 1 < levels.length) { setLevel(level + 1); } else { alert(बधाई हो! आपने Fruitopia में ${score + 10} XP अर्जित किए।); setLevel(0); setScore(0); } }, 1000); };

return ( <div className="p-6 max-w-xl mx-auto text-center"> <h1 className="text-2xl font-bold mb-4">🌱 Fruitopia Game</h1> <Card className="mb-4"> <CardContent> <h2 className="text-xl font-semibold mb-2">{current.title}</h2> <p className="mb-4">{current.question}</p> <div className="space-y-2"> {current.options.map((option, i) => ( <Button key={i} variant={selected === i ? (i === current.answer ? "default" : "destructive") : "outline"} onClick={() => handleAnswer(i)} className="w-full" > {option} </Button> ))} </div> </CardContent> </Card> <p>🎖️ XP: {score}</p> </div> ); }

