import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";

export default function AirlineBookingApp() {
  const [visaCheck, setVisaCheck] = useState({ nationality: "", destination: "", result: "" });

  const checkVisaEligibility = () => {
    if (visaCheck.nationality && visaCheck.destination) {
      if (visaCheck.nationality === "USA" && visaCheck.destination === "UK") {
        setVisaCheck({ ...visaCheck, result: "Visa required. Apply before travel." });
      } else {
        setVisaCheck({ ...visaCheck, result: "Visa not required for short stays." });
      }
    }
  };

  return (
    <div className="p-4 max-w-2xl mx-auto">
      <h1 className="text-2xl font-bold mb-4">Airline Booking & Visa Checker</h1>
      <Card>
        <CardContent className="p-4">
          <h2 className="text-xl font-semibold mb-3">Visa Eligibility Checker</h2>
          <Input
            placeholder="Enter your nationality"
            value={visaCheck.nationality}
            onChange={(e) => setVisaCheck({ ...visaCheck, nationality: e.target.value })}
            className="mb-2"
          />
          <Input
            placeholder="Enter your destination"
            value={visaCheck.destination}
            onChange={(e) => setVisaCheck({ ...visaCheck, destination: e.target.value })}
            className="mb-2"
          />
          <Button onClick={checkVisaEligibility} className="mt-2">Check Visa</Button>
          {visaCheck.result && <p className="mt-2 font-medium">{visaCheck.result}</p>}
        </CardContent>
      </Card>
    </div>
  );
}
