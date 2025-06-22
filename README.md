import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import { Textarea } from "@/components/ui/textarea";
import { motion } from "framer-motion";

export default function PrivateReservePage() {
  const [ageConfirmed, setAgeConfirmed] = useState(false);
  const [showPopup, setShowPopup] = useState(true);

  const confirmAge = () => {
    setAgeConfirmed(true);
    setShowPopup(false);
  };

  if (showPopup) {
    return (
      <div className="fixed inset-0 bg-black bg-opacity-80 flex items-center justify-center z-50">
        <div className="bg-white p-6 rounded-2xl text-center max-w-sm w-full">
          <h2 className="text-xl font-bold mb-4">Bekræft din alder</h2>
          <p className="mb-4">Du skal være over 18 år for at besøge denne side.</p>
          <Button onClick={confirmAge} className="w-full">Jeg er over 18 år</Button>
        </div>
      </div>
    );
  }

  return (
    <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="p-4 max-w-5xl mx-auto">
      <h1 className="text-4xl font-bold mb-6 text-center">Private Reserve – Eksklusiv Spiritussamling</h1>

      <div className="grid grid-cols-1 md:grid-cols-2 gap-6 mb-10">
        <Card>
          <CardContent className="p-4">
            <img src="/grey-goose.jpg" alt="Grey Goose" className="rounded-2xl mb-4" />
            <h2 className="text-2xl font-semibold">Grey Goose Vodka – 1L</h2>
            <p className="text-base mt-2">Elegant fransk vodka – kendt for sin bløde og rene smag. Perfekt til særlige lejligheder.</p>
          </CardContent>
        </Card>

        <Card>
          <CardContent className="p-4">
            <img src="/gold-stoli.jpg" alt="Gold Stoli" className="rounded-2xl mb-4" />
            <h2 className="text-2xl font-semibold">Gold Stoli Vodka – 1L</h2>
            <p className="text-base mt-2">Eksklusiv udgave af Stolichnaya – fyldig karakter med gylden elegance.</p>
          </CardContent>
        </Card>
      </div>

      <div className="bg-white shadow-md rounded-2xl p-6">
        <h2 className="text-2xl font-bold mb-4">Kontakt mig</h2>
        <form className="grid gap-4">
          <Input placeholder="Navn" required />
          <Input placeholder="Email" type="email" required />
          <Textarea placeholder="Din besked..." required />
          <Button type="submit">Send besked</Button>
        </form>
      </div>
    </motion.div>
  );
}
