import React, { useState } from 'react';
import { Gift, Sparkles, ChevronRight } from 'lucide-react';

const giftData = {
  friend: {
    low: [
      "🎄 Ho ho ho! A cozy pair of holiday socks with hot cocoa mix will warm their toes and their heart! Perfect for those chilly winter nights by the fire!",
      "🌟 Santa suggests a festive scented candle and a handwritten letter sharing your favorite memories together! Nothing says friendship like the gift of nostalgia!",
      "🎁 A DIY cookie decorating kit with Santa's special recipe will bring out their inner elf! Sweet treats make the merriest memories!",
      "⛄ How about a fun Christmas ornament that captures an inside joke you share? Every year they'll hang it and think of you!",
      "🎅 A mini succulent in a holiday planter with googly eyes will bring year-round cheer! Even Santa's elves love low-maintenance plants!",
      "🔔 A festive mug filled with their favorite tea or coffee blend is a hug in a cup! Bonus points for adding marshmallows!",
      "❄️ Santa recommends a cute holiday keychain and a gift card to their favorite coffee shop! Small but mighty, just like Rudolph's nose!",
      "🎄 A bookmark shaped like a candy cane with a bestselling paperback is perfect for your bookworm buddy! Reading by the fire is pure Christmas magic!",
      "🌟 A set of holiday-themed stickers or washi tape will spark their creative spirit! Even Santa's workshop needs fun supplies!",
      "🎁 How about bath bombs in festive scents like peppermint or cinnamon? Self-care is on Santa's nice list!"
    ],
    medium: [
      "🎅 A personalized photo calendar filled with your adventures together will make every month magical! Santa loves when friends cherish memories!",
      "🎄 A cozy weighted blanket for ultimate Netflix-and-chill winter nights is on my nice list! Snuggle season just got an upgrade!",
      "⛄ Santa suggests a trendy portable Bluetooth speaker for their holiday parties and road trips! Music makes everything merrier!",
      "🌟 A beautiful houseplant like a fiddle leaf fig with a decorative pot brings life to any space! Growing friendships deserve growing greens!",
      "🎁 A subscription box for their hobby—coffee, books, snacks, or skincare—keeps the Christmas spirit going all year! The gift that keeps on giving!",
      "🔔 How about a stylish water bottle and a fitness class pass to help them crush their New Year goals? Santa supports healthy habits!",
      "❄️ A deluxe board game or puzzle for cozy game nights will create memories worth more than gold! Competition is Santa-approved!",
      "🎄 A chic tote bag or backpack in their favorite color combines style with practicality! Even elves need fashionable carry-alls!",
      "🎅 Santa recommends wireless earbuds for their commute, workouts, or downtime! Quality sound is a gift they'll use daily!",
      "🌟 A gourmet food basket with artisan cheeses, crackers, and treats makes every gathering festive! Sharing is caring, after all!"
    ],
    high: [
      "🎁 A smartwatch to track their fitness and stay connected is tech Santa approves! The future is merry and bright!",
      "🎄 How about a weekend getaway voucher to a cozy cabin or spa resort? Adventures make the best presents!",
      "⛄ Santa suggests a high-quality espresso machine for the coffee lover who deserves barista-level brews at home! Wake up to Christmas every morning!",
      "🌟 A designer handbag or wallet they've been eyeing will make them feel like they're on the nice list! Luxury never goes out of style!",
      "🎅 A professional photography session to capture your friendship is a gift that lasts forever! Memories framed in gold!",
      "🔔 How about the latest gaming console or VR headset for epic entertainment? Play time is the best time!",
      "❄️ A premium standing desk or ergonomic office chair shows you care about their comfort! Santa supports good posture!",
      "🎄 A top-tier noise-canceling headphones set will give them peace in any chaos! The gift of silence is golden!",
      "🎁 Santa recommends a high-end kitchen appliance like an air fryer or stand mixer for the culinary enthusiast! Home-cooked magic awaits!",
      "🌟 A luxury skincare or grooming set from their dream brand is self-care wrapped in a bow! Everyone deserves to feel pampered!"
    ]
  },
  sibling: {
    low: [
      "🎅 A hilarious inside-joke mug that only you two understand will start their mornings with laughter! Sibling humor is the best humor!",
      "🎄 Santa suggests scratch-off lottery tickets tucked in a funny card—who knows, they might win big! Fortune favors the festive!",
      "⛄ A pack of their favorite candy from childhood will bring back sweet memories! Nostalgia tastes delicious!",
      "🌟 How about a quirky desk accessory like a mini zen garden or stress ball? Even siblings need to decompress!",
      "🎁 A fun pair of novelty socks with their favorite animal or hobby on them is cozy and comedic! Socks are always a win!",
      "🔔 Santa recommends a DIY craft kit for friendship bracelets or paint-by-numbers! Create something together this holiday!",
      "❄️ A festive phone case or pop socket in their style keeps them protected and merry! Practical meets personal!",
      "🎄 How about a small potted herb garden for their kitchen windowsill? Fresh basil makes everything better!",
      "🎅 A funny or inspirational book under $15 that matches their sense of humor is perfect! Knowledge wrapped in joy!",
      "🌟 Santa suggests movie theater gift cards for a sibling movie date night! Popcorn and bonding time await!"
    ],
    medium: [
      "🎁 A cozy hoodie or sweatshirt in their favorite color is like a wearable hug from you! Comfort level: maximum!",
      "🎄 Santa recommends a vinyl record or special edition album from their favorite artist! Music is the soundtrack of siblinghood!",
      "⛄ How about a quality kitchen gadget like an instant-read thermometer or knife set for the aspiring chef? Cook up some fun!",
      "🌟 A stylish watch or piece of jewelry they can wear every day keeps you close to their heart! Timeless and touching!",
      "🎅 Santa suggests a streaming service subscription for a year of binge-worthy content together! Netflix and sibling bonding!",
      "🔔 A personalized cutting board or engraved item with a funny sibling quote will last forever! Laughter is forever!",
      "❄️ How about a beginner-friendly musical instrument like a ukulele or keyboard? Make some noise this Christmas!",
      "🎄 A high-quality backpack or gym bag for their active lifestyle is both practical and thoughtful! Adventure awaits!",
      "🎁 Santa recommends an experience gift like concert tickets or an escape room adventure! Memories over material things!",
      "🌟 A Bluetooth label maker for the organized sibling is oddly satisfying and supremely useful! Organization is celebration!"
    ],
    high: [
      "🎅 A laptop or tablet to help them crush school or work goals shows you believe in their dreams! Technology with love!",
      "🎄 How about a premium bicycle or electric scooter for eco-friendly adventures? Ride into the new year with style!",
      "⛄ Santa suggests a DSLR camera or GoPro for the sibling who loves capturing life's moments! Picture-perfect presents!",
      "🌟 A designer jacket or coat they've been dreaming about will keep them warm and fashionable! Winter just got an upgrade!",
      "🎁 How about furniture for their first apartment like a comfy reading chair or bookshelf? Adulting made easier!",
      "🔔 Santa recommends the latest smartphone or wireless earbuds they've been eyeing! Stay connected in style!",
      "❄️ A high-end coffee maker or espresso machine for the caffeine enthusiast is pure liquid gold! Wake up happy!",
      "🎄 How about paying for a certification course or workshop in something they're passionate about? Invest in their future!",
      "🎅 A luxury luggage set for the sibling with wanderlust will carry them to amazing places! Adventure is calling!",
      "🌟 Santa suggests a home gym equipment package like weights or a yoga set-up! Fitness goals start here!"
    ]
  },
  parent: {
    low: [
      "🎄 A heartfelt handwritten letter sharing what they mean to you is priceless! Santa knows love beats everything!",
      "🎅 How about their favorite specialty coffee or tea with a festive mug? Cozy sips bring warm feelings!",
      "⛄ A framed photo of a cherished family moment will brighten any room! Memories are the best decorations!",
      "🌟 Santa suggests a pretty succulent or small plant to brighten their workspace! Green thumbs bring green joy!",
      "🎁 A homemade coupon book offering to do chores, cook dinner, or spend quality time is pure gold! Time is the greatest gift!",
      "🔔 How about a festive holiday candle in their favorite scent like vanilla or pine? Ambiance is everything!",
      "❄️ A cooking or baking ingredient set with premium spices or vanilla extract upgrades their kitchen game! Flavor town awaits!",
      "🎄 Santa recommends a beautiful bookmark and a bestselling novel in their favorite genre! Reading time is sacred!",
      "🎅 A car air freshener and window cleaner kit keeps their ride fresh and clean! Practical love shines!",
      "🌟 How about a scratch-off world map or USA map to track their travels? Adventure documented beautifully!"
    ],
    medium: [
      "🎁 A luxurious throw blanket for couch cuddles and movie marathons is comfort perfected! Every parent deserves cozy!",
      "🎄 Santa suggests a digital photo frame preloaded with family pictures that rotate automatically! Tech meets heart!",
      "⛄ How about a quality kitchen appliance like a slow cooker or air fryer? Home cooking just got easier!",
      "🌟 A spa gift basket with bath salts, lotions, and face masks says 'you deserve relaxation!' Self-care is essential!",
      "🎅 Santa recommends a stylish insulated tumbler that keeps drinks perfect for hours! Hydration meets fashion!",
      "🔔 How about a beautiful piece of wall art or family name sign for their home? Personalized décor warms hearts!",
      "❄️ A subscription to their favorite magazine or streaming service keeps entertainment coming all year! Joy delivered monthly!",
      "🎄 Santa suggests noise-canceling headphones for peaceful moments or audiobook listening! Peace and quiet, served!",
      "🎁 How about a high-quality chef's knife or cooking tool set for the parent who loves to cook? Sharp gifts cut through!",
      "🌟 A personalized cutting board with family names or a sweet message is functional art! Kitchen love forever!"
    ],
    high: [
      "🎅 A smart home device like a robot vacuum or smart thermostat makes life easier! Technology they'll thank you for daily!",
      "🎄 How about a weekend spa retreat or hotel getaway for much-deserved rest and relaxation? They've earned paradise!",
      "⛄ Santa suggests a high-quality recliner or massage chair for ultimate comfort! Relaxation station achieved!",
      "🌟 A professional family photo session captures everyone together beautifully! Memories preserved forever!",
      "🎁 How about the latest iPad or tablet for entertainment, reading, and staying connected? Modern convenience wrapped up!",
      "🔔 Santa recommends a premium coffee machine with a grinder for café-quality mornings at home! Barista-level love!",
      "❄️ A luxury watch or piece of jewelry they'll treasure forever shows your appreciation! Timeless elegance!",
      "🎄 How about new patio furniture or a fire pit for family gatherings? Create backyard memories!",
      "🎅 Santa suggests a high-end sound system or smart TV for movie nights elevated! Entertainment headquarters unlocked!",
      "🌟 A contribution toward their dream vacation or cruise makes their bucket list dreams come true! Adventure awaits!"
    ]
  },
  bestfriend: {
    low: [
      "🎄 A friendship bracelet you made yourself shows effort and love! Handmade beats store-bought every time!",
      "🎅 Santa suggests a mini photo album filled with your favorite memories together! Nostalgia in your pocket!",
      "⛄ How about matching keychains or pins that represent your inside jokes? Twinning is winning!",
      "🌟 A fun card game or mini puzzle for your next hangout creates instant entertainment! Game on, besties!",
      "🎁 Santa recommends their favorite snack or candy in bulk because you know them that well! Sugar and friendship forever!",
      "🔔 How about a funny or inspirational magnet for their fridge? Daily smiles delivered!",
      "❄️ A festive scrunchie or hair accessory set keeps them stylish and merry! Fashion meets function!",
      "🎄 Santa suggests a decorated mason jar filled with handwritten notes of why they're amazing! 365 days of love!",
      "🎅 How about a coloring book and gel pens for stress-free creative time together? Art therapy unlocked!",
      "🌟 A custom playlist on a USB drive or burned CD with songs that remind you of them is pure nostalgia! Music is friendship!"
    ],
    medium: [
      "🎁 A matching set of something you both love—mugs, t-shirts, or pajamas—celebrates your bond! Twinning goals achieved!",
      "🎄 Santa recommends a quality journal or planner to help them organize their dreams! Write the future!",
      "⛄ How about a skincare or self-care set with face masks and serums? Glow together, bestie!",
      "🌟 A polaroid camera or instant camera for capturing spontaneous memories is pure magic! Every moment documented!",
      "🎅 Santa suggests a cozy blanket hoodie for maximum comfort during your movie marathons! Wearable heaven!",
      "🔔 How about a 'Best Friend' necklace set or matching jewelry you both can wear? Hearts connected!",
      "❄️ A beautiful planner or bullet journal with stickers and pens fuels their creativity! Organization is art!",
      "🎄 Santa recommends an experience like a cooking class or pottery workshop you do together! Make memories, not just gifts!",
      "🎁 How about a high-quality reusable water bottle with stickers you personalize? Hydration with personality!",
      "🌟 A curated book with a heartfelt inscription about your friendship lives on their shelf forever! Words that matter!"
    ],
    high: [
      "🎅 Matching designer sneakers or shoes you've both been wanting? Walk through life together in style! Fresh kicks, fresh friendship!",
      "🎄 Santa suggests a luxurious weekend trip or concert tickets to see your favorite artist! Adventures are everything!",
      "⛄ How about the latest tech gadget like AirPods or a smartwatch? Stay connected in style!",
      "🌟 A professional photoshoot for both of you captures your friendship forever! Picture perfect besties!",
      "🎁 Santa recommends a high-end handbag or accessory they've been dreaming about! Dreams do come true!",
      "🔔 How about a year-long subscription box tailored to their interests—beauty, books, or snacks? Monthly surprises!",
      "❄️ A premium piece of jewelry like a bracelet or necklace with both your initials bonds you forever! Elegance meets emotion!",
      "🎄 Santa suggests a top-tier kitchen appliance for the foodie bestie like a stand mixer! Baking together elevated!",
      "🎅 How about a designer backpack or travel bag for your future adventures together? Pack up the memories!",
      "🌟 A contribution to something meaningful they're saving for shows you believe in their dreams! Support wrapped with love!"
    ]
  }
};

export default function SantaGiftGenerator() {
  const [recipient, setRecipient] = useState('');
  const [budget, setBudget] = useState('');
  const [gift, setGift] = useState('');
  const [isGenerating, setIsGenerating] = useState(false);
  const [showResult, setShowResult] = useState(false);

  const generateGift = () => {
    if (!recipient || !budget) return;
    
    setIsGenerating(true);
    setShowResult(false);
    
    setTimeout(() => {
      const gifts = giftData[recipient][budget];
      const randomGift = gifts[Math.floor(Math.random() * gifts.length)];
      setGift(randomGift);
      setIsGenerating(false);
      setShowResult(true);
    }, 1500);
  };

  const reset = () => {
    setRecipient('');
    setBudget('');
    setGift('');
    setShowResult(false);
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-red-600 via-red-700 to-green-800 flex items-center justify-center p-4">
      <div className="absolute inset-0 overflow-hidden pointer-events-none">
        {[...Array(50)].map((_, i) => (
          <div
            key={i}
            className="absolute text-white opacity-20 animate-pulse"
            style={{
              left: `${Math.random() * 100}%`,
              top: `${Math.random() * 100}%`,
              animationDelay: `${Math.random() * 3}s`,
              fontSize: `${Math.random() * 20 + 10}px`
            }}
          >
            ❄️
          </div>
        ))}
      </div>

      <div className="max-w-2xl w-full bg-white rounded-3xl shadow-2xl p-8 relative z-10">
        <div className="text-center mb-8">
          <div className="flex items-center justify-center mb-4">
            <Gift className="w-16 h-16 text-red-600 animate-bounce" />
          </div>
          <h1 className="text-4xl font-bold text-red-600 mb-2">
            Santa's Instant Gift Generator
          </h1>
          <p className="text-gray-600">Ho ho ho! Let Santa help you find the perfect gift! 🎅</p>
        </div>

        {!showResult ? (
          <div className="space-y-6">
            <div>
              <label className="block text-lg font-semibold text-gray-700 mb-3">
                Who's the lucky person? 🎁
              </label>
              <div className="grid grid-cols-2 gap-3">
                {[
                  { value: 'friend', label: '👥 Friend', emoji: '👥' },
                  { value: 'sibling', label: '👫 Sibling', emoji: '👫' },
                  { value: 'parent', label: '👨‍👩‍👦 Parent', emoji: '👨‍👩‍👦' },
                  { value: 'bestfriend', label: '💖 Best Friend', emoji: '💖' }
                ].map((option) => (
                  <button
                    key={option.value}
                    onClick={() => setRecipient(option.value)}
                    className={`p-4 rounded-xl border-2 transition-all transform hover:scale-105 ${
                      recipient === option.value
                        ? 'border-red-600 bg-red-50 shadow-lg'
                        : 'border-gray-200 hover:border-red-300'
                    }`}
                  >
                    <div className="text-3xl mb-1">{option.emoji}</div>
                    <div className="font-semibold text-gray-700">
                      {option.label.split(' ')[1]}
                    </div>
                  </button>
                ))}
              </div>
            </div>

            <div>
              <label className="block text-lg font-semibold text-gray-700 mb-3">
                What's your budget? 💰
              </label>
              <div className="grid grid-cols-3 gap-3">
                {[
                  { value: 'low', label: 'Budget Friendly', emoji: '💵', range: '$0-25' },
                  { value: 'medium', label: 'Moderate', emoji: '💳', range: '$25-100' },
                  { value: 'high', label: 'Luxurious', emoji: '💎', range: '$100+' }
                ].map((option) => (
                  <button
                    key={option.value}
                    onClick={() => setBudget(option.value)}
                    className={`p-4 rounded-xl border-2 transition-all transform hover:scale-105 ${
                      budget === option.value
                        ? 'border-green-600 bg-green-50 shadow-lg'
                        : 'border-gray-200 hover:border-green-300'
                    }`}
                  >
                    <div className="text-3xl mb-1">{option.emoji}</div>
                    <div className="font-semibold text-gray-700 text-sm">
                      {option.label}
                    </div>
                    <div className="text-xs text-gray-500">{option.range}</div>
                  </button>
                ))}
              </div>
            </div>

            <button
              onClick={generateGift}
              disabled={!recipient || !budget || isGenerating}
              className={`w-full py-4 rounded-xl font-bold text-lg transition-all transform ${
                recipient && budget && !isGenerating
                  ? 'bg-gradient-to-r from-red-600 to-green-600 text-white hover:scale-105 hover:shadow-xl'
                  : 'bg-gray-300 text-gray-500 cursor-not-allowed'
              }`}
            >
              {isGenerating ? (
                <span className="flex items-center justify-center">
                  <Sparkles className="w-5 h-5 mr-2 animate-spin" />
                  Santa is thinking...
                </span>
              ) : (
                <span className="flex items-center justify-center">
                  Generate Gift Idea
                  <ChevronRight className="w-5 h-5 ml-2" />
                </span>
              )}
            </button>
          </div>
        ) : (
          <div className="space-y-6">
            <div className="bg-gradient-to-br from-red-50 to-green-50 rounded-2xl p-6 border-2 border-red-200">
              <div className="text-center mb-4">
                <Sparkles className="w-12 h-12 text-yellow-500 mx-auto mb-2 animate-pulse" />
                <h2 className="text-2xl font-bold text-red-700">
                  Santa's Perfect Pick!
                </h2>
              </div>
              <p className="text-lg leading-relaxed text-gray-800">
                {gift}
              </p>
            </div>

            <div className="flex gap-3">
              <button
                onClick={generateGift}
                className="flex-1 py-3 rounded-xl font-semibold bg-green-600 text-white hover:bg-green-700 transition-all transform hover:scale-105"
              >
                🎲 Try Another Gift
              </button>
              <button
                onClick={reset}
                className="flex-1 py-3 rounded-xl font-semibold bg-red-600 text-white hover:bg-red-700 transition-all transform hover:scale-105"
              >
                🔄 Start Over
              </button>
            </div>
          </div>
        )}

        <div className="mt-8 text-center text-sm text-gray-500">
          Made with ❤️ for the holidays • Powered by Santa's Workshop 🎅
        </div>
      </div>
    </div>
  );
}
