# PROJECT NO-1
// AI Resume & Interview Prep Platform (MVP Version)

import React, { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Textarea } from "@/components/ui/textarea"; import { Input } from "@/components/ui/input"; import { Sparkles } from "lucide-react";

export default function ResumeInterviewApp() { const [resumeInput, setResumeInput] = useState(""); const [aiResume, setAiResume] = useState(""); const [interviewQn, setInterviewQn] = useState([]); const [loading, setLoading] = useState(false);

const generateResume = async () => { setLoading(true); const prompt = Create a modern, professional resume for this info: ${resumeInput}; const response = await fetch("https://api.openai.com/v1/chat/completions", { method: "POST", headers: { "Content-Type": "application/json", Authorization: Bearer YOUR_OPENAI_API_KEY }, body: JSON.stringify({ model: "gpt-4", messages: [{ role: "user", content: prompt }] }) }); const data = await response.json(); setAiResume(data.choices[0].message.content); setLoading(false); };

const getInterviewQuestions = async () => { setLoading(true); const prompt = Give 5 common interview questions for someone applying as: ${resumeInput}; const response = await fetch("https://api.openai.com/v1/chat/completions", { method: "POST", headers: { "Content-Type": "application/json", Authorization: Bearer YOUR_OPENAI_API_KEY }, body: JSON.stringify({ model: "gpt-4", messages: [{ role: "user", content: prompt }] }) }); const data = await response.json(); const text = data.choices[0].message.content; setInterviewQn(text.split("\n").filter((q) => q)); setLoading(false); };

return ( <div className="max-w-2xl mx-auto p-4 space-y-4"> <Card className="p-4"> <CardContent> <h1 className="text-xl font-bold mb-2">AI

