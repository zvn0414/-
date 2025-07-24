import React, { useState } from "react"; import { Input } from "@/components/ui/input"; import { Button } from "@/components/ui/button"; import { Card, CardContent } from "@/components/ui/card";

const ProductionTimeCalculator = () => { const [currentProduction, setCurrentProduction] = useState(0); const [endTime, setEndTime] = useState<string | null>(null);

const calculateEndTime = () => { const currentBoxes = currentProduction / 20; const remainingBoxes = currentBoxes - 480; const remainingTimeInHours = remainingBoxes / 1.4; const now = new Date(); const end = new Date(now.getTime() + remainingTimeInHours * 60 * 60 * 1000); setEndTime(end.toLocaleString()); };

return ( <div className="max-w-md mx-auto mt-10 p-4"> <Card className="p-6 shadow-xl"> <CardContent className="flex flex-col gap-4"> <h1 className="text-xl font-bold">生産終了時刻計算アプリ</h1> <Input type="number" placeholder="現在の生産数を入力" value={currentProduction} onChange={(e) => setCurrentProduction(Number(e.target.value))} /> <Button onClick={calculateEndTime}>終了時刻を計算</Button> {endTime && ( <div className="text-green-700 font-semibold"> 生産終了時刻: {endTime} </div> )} </CardContent> </Card> </div> ); };

export default ProductionTimeCalculator;

