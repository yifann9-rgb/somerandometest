# somerandometest
just a test
export default function aPersonalityTest() {
  const questions = [
    {
      title: '1. Zombie Apocalypse...',
      options: {
        A: 'Join the strongest zombie and climb the undead corporate ladder.',
        B: 'Lock the doors, enjoy the last moments, and choose your date to commit suicide.',
        C: ' Join a survivor camp and become the boss favourate kid.',
        D: 'Steal an RV and go on a zombie road trip.'
      }
    },
    {
      title: '2. Bank Robbery, you re the staff',
      options: {
        A: ' Offer the vault code for a commission. Secretly steal the most expensive dimond',
        B: 'Hide and poop in the toilet, and hoping you too stink to approach.',
        C: 'Took the nearest customer hostage, demonstrate excellent skills, turn the scene to a job interview.',
        D: 'Help people escape when the opportunity appears, and ask $100 each to buy their life.'
      }
    },
    {
      title: "3. Friend's Dirty Secret. ohHor!She/he dating your another freind found touching a old rich man's buttock on street",
      options: {
        A: 'Take a photo. This looks expensive. Blackmail the old man 10k via your friend, and promise a 5/5 with your freind',
        B: 'Pretend I saw nothing, and talk to chatgpt.',
        C: 'Let your friend introduce more rich man to you also',
        D: 'Confront them directly, and send a "one should not betray everything for money" reel on tiktok.'
      }
    },
    {
      title: '4. Final Project Disaster: your mentor got jealouse of  your talenet and destroy your work?',
      options: {
        A: 'Secure evidence first, blackmail your mentor for travel funds.',
        B: 'Ask chatgpt "what should i do now?"',
        C: 'Burn the school, now evreyone need to redo their work.',
        D: 'Exhibit it your draft and thereaten your mentor to give you a A.'
      }
    }
  ];

  const personalities = {
    A: {
      title: 'The Opportunist',
      text: 'You turn chaos into opportunity and always spot potential advantages before everyone else.'
    },
    B: {
      title: 'The Survivor',
      text: 'You avoid unnecessary drama and somehow outlast everyone with minimal effort.'
    },
    C: {
      title: 'The Strategist',
      text: 'Your greatest weapon is people. Networking and diplomacy solve almost everything.'
    },
    D: {
      title: 'The Maverick',
      text: 'You act boldly, improvise constantly, and somehow make impossible plans work.'
    }
  };

  const [answers, setAnswers] = React.useState({});
  const [result, setResult] = React.useState(null);

  const calculate = () => {
    if (Object.keys(answers).length !== questions.length) {
      alert('Please answer every question.');
      return;
    }

    const scores = { A: 0, B: 0, C: 0, D: 0 };
    Object.values(answers).forEach(v => scores[v]++);

    const winner = Object.keys(scores).reduce((a, b) =>
      scores[a] >= scores[b] ? a : b
    );

    setResult(personalities[winner]);
  };

  return (
    <div className="min-h-screen bg-gray-100 p-6">
      <div className="max-w-4xl mx-auto">
        <div className="bg-white rounded-3xl shadow-lg p-8 mb-6">
          <h1 className="text-4xl font-bold text-center mb-4">
            A Personality Test
          </h1>
          <p className="text-center text-gray-600">
            Welcome. Choose the answer that feels most like you.
          </p>
        </div>

        {questions.map((q, index) => (
          <div key={index} className="bg-white rounded-2xl shadow p-6 mb-5">
            <h2 className="text-xl font-semibold mb-4">{q.title}</h2>
            <div className="space-y-3">
              {Object.entries(q.options).map(([key, value]) => (
                <label key={key} className="flex gap-3 cursor-pointer p-3 rounded-xl hover:bg-gray-50">
                  <input
                    type="radio"
                    name={`q${index}`}
                    checked={answers[index] === key}
                    onChange={() =>
                      setAnswers({ ...answers, [index]: key })
                    }
                  />
                  <span>{value}</span>
                </label>
              ))}
            </div>
          </div>
        ))}

        <div className="text-center">
          <button
            onClick={calculate}
            className="bg-black text-white px-8 py-3 rounded-2xl hover:bg-gray-800"
          >
            Reveal My Personality
          </button>
        </div>

        {result && (
          <div className="bg-white rounded-3xl shadow-lg p-8 mt-8">
            <h2 className="text-3xl font-bold mb-4">{result.title}</h2>
            <p className="text-lg text-gray-700">{result.text}</p>
          </div>
        )}
      </div>
    </div>
  );
}
