import React, { useState } from "react";
import "./styles.css";

export default function App() {
  // State variables
  const [numDogs, setNumDogs] = useState(1);
  const [boardingHoliday, setBoardingHoliday] = useState(0);
  const [boardingNonHoliday, setBoardingNonHoliday] = useState(0);
  const [boardingStays, setBoardingStays] = useState(0); // NEW: Boarding stays count
  const [daycareDays, setDaycareDays] = useState(0);
  const [bathsCount, setBathsCount] = useState(0);
  const [bathSize, setBathSize] = useState("30");
  const [additionalFees, setAdditionalFees] = useState(0);
  const [medicationDays, setMedicationDays] = useState(0); // NEW: Medication
  const [dosesPerDay, setDosesPerDay] = useState(0); // NEW: Medication

  const calculateSavings = () => {
    const bathPrice = parseInt(bathSize);

    // NEW TRANSPORTATION CALCULATIONS
    const daycareTransportCost = daycareDays * 10; // Auto $10/day
    const boardingTransportCost = boardingStays * 20; // $20 per stay

    // NEW MEDICATION COST
    const medicationCost = medicationDays * dosesPerDay * 5;

    // --- Without Subscription ---
    const boardingHolidayCostWithout = (75 + 5) * numDogs * boardingHoliday;
    const boardingNonHolidayCostWithout = 60 * numDogs * boardingNonHoliday;
    const additionalFeesCost =
      additionalFees * numDogs * (boardingHoliday + boardingNonHoliday);

    let daycareCostWithout =
      numDogs === 1 ? 42 * daycareDays : 42 * numDogs * 0.85 * daycareDays;

    const transportCostWithout = daycareTransportCost + boardingTransportCost;
    const bathsCostWithout = bathsCount * bathPrice;

    const totalWithout =
      boardingHolidayCostWithout +
      boardingNonHolidayCostWithout +
      daycareCostWithout +
      transportCostWithout +
      bathsCostWithout +
      additionalFeesCost +
      medicationCost;

    // --- Standard Subscription ---
    const standardFee = 100 + Math.max(numDogs - 1, 0) * 25;
    const boardingHolidayStandard = (65 + 5) * numDogs * boardingHoliday;
    const boardingNonHolidayStandard = 55 * numDogs * boardingNonHoliday;

    let daycareStandard =
      38 * (numDogs === 1 ? daycareDays : numDogs * 0.85 * daycareDays);
    const bathsStandard = bathsCount * bathPrice * 0.6;

    // Transport costs $0 with subscription
    const totalStandard =
      boardingHolidayStandard +
      boardingNonHolidayStandard +
      daycareStandard +
      bathsStandard +
      additionalFeesCost +
      standardFee +
      medicationCost;

    // --- Premium Subscription ---
    const premiumFee = 135 + Math.max(numDogs - 1, 0) * 30;
    const boardingHolidayPremium = 55 * numDogs * boardingHoliday;
    const boardingNonHolidayPremium = 55 * numDogs * boardingNonHoliday;

    const totalPremium =
      boardingHolidayPremium +
      boardingNonHolidayPremium +
      daycareStandard +
      additionalFeesCost +
      premiumFee +
      medicationCost;

    return {
      totalWithout: totalWithout.toFixed(2),
      totalStandard: totalStandard.toFixed(2),
      totalPremium: totalPremium.toFixed(2),
      savingsStandard: (totalWithout - totalStandard).toFixed(2),
      savingsPremium: (totalWithout - totalPremium).toFixed(2),
    };
  };

  const results = calculateSavings();

  return (
    <div className="App">
      <h1>Subscription Savings Calculator</h1>

      <div className="input-group">
        <label>Number of Dogs:</label>
        <input
          type="number"
          value={numDogs}
          onChange={(e) => setNumDogs(Math.max(1, e.target.value))}
        />
      </div>

      {/* BOARDING SECTION */}
      <div className="section">
        <h3>Boarding</h3>
        <div className="input-group">
          <label>Holiday Nights:</label>
          <input
            type="number"
            value={boardingHoliday}
            onChange={(e) => setBoardingHoliday(Math.max(0, e.target.value))}
          />
        </div>
        <div className="input-group">
          <label>Non-Holiday Nights:</label>
          <input
            type="number"
            value={boardingNonHoliday}
            onChange={(e) => setBoardingNonHoliday(Math.max(0, e.target.value))}
          />
        </div>
        {/* NEW BOARDING STAYS INPUT */}
        <div className="input-group">
          <label>Number of Boarding Stays:</label>
          <input
            type="number"
            value={boardingStays}
            onChange={(e) => setBoardingStays(Math.max(0, e.target.value))}
          />
        </div>
      </div>

      {/* DAYCARE SECTION */}
      <div className="section">
        <h3>Daycare</h3>
        <div className="input-group">
          <label>Days Needed:</label>
          <input
            type="number"
            value={daycareDays}
            onChange={(e) => setDaycareDays(Math.max(0, e.target.value))}
          />
        </div>
      </div>

      {/* ADDITIONAL COSTS SECTION */}
      <div className="section">
        <h3>Additional Costs</h3>
        <div className="input-group">
          <label>Baths per Month:</label>
          <input
            type="number"
            value={bathsCount}
            onChange={(e) => setBathsCount(Math.max(0, e.target.value))}
          />
        </div>
        <div className="input-group">
          <label>Bath Size:</label>
          <select
            value={bathSize}
            onChange={(e) => setBathSize(e.target.value)}
          >
            <option value="20">Small ($20)</option>
            <option value="30">Medium ($30)</option>
            <option value="40">Large ($40)</option>
            <option value="50">Extra Large ($50)</option>
          </select>
        </div>
        <div className="input-group">
          <label>Additional Fees per Night:</label>
          <input
            type="number"
            value={additionalFees}
            onChange={(e) => setAdditionalFees(Math.max(0, e.target.value))}
          />
        </div>
        {/* NEW MEDICATION INPUTS */}
        <div className="input-group">
          <label>Days Needing Medication:</label>
          <input
            type="number"
            value={medicationDays}
            onChange={(e) => setMedicationDays(Math.max(0, e.target.value))}
          />
        </div>
        <div className="input-group">
          <label>Doses Per Day:</label>
          <input
            type="number"
            value={dosesPerDay}
            onChange={(e) => setDosesPerDay(Math.max(0, e.target.value))}
          />
        </div>
      </div>

      {/* RESULTS SECTION */}
      <div className="results">
        <h2>Results</h2>
        <div className="result-card">
          <h3>Without Subscription: ${results.totalWithout}</h3>
        </div>
        <div className="result-card">
          <h3>Standard Subscription</h3>
          <p>Total Cost: ${results.totalStandard}</p>
          <p>Savings: ${results.savingsStandard}</p>
          <p>Break-Even: {results.savingsStandard >= 0 ? "✅ Yes" : "❌ No"}</p>
        </div>
        <div className="result-card">
          <h3>Premium Subscription</h3>
          <p>Total Cost: ${results.totalPremium}</p>
          <p>Savings: ${results.savingsPremium}</p>
          <p>Break-Even: {results.savingsPremium >= 0 ? "✅ Yes" : "❌ No"}</p>
        </div>
      </div>
    </div>
  );
}
