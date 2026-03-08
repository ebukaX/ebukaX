import { useState, useEffect } from "react";

const typewriterPhrases = [
  "Information Systems Student 🎓",
  "Vibe Coder ✨",
  "Data & ML Curious 🤖",
  "Cybersecurity Curious 🔐",
  "Psychology Enthusiast 🧠",
  "Full-time Idea Machine 💡",
  "Open to Mentorship 🙌",
];

export default function EbukaProfile() {
  const [displayed, setDisplayed] = useState("");
  const [phraseIndex, setPhraseIndex] = useState(0);
  const [charIndex, setCharIndex] = useState(0);
  const [deleting, setDeleting] = useState(false);
  const [blink, setBlink] = useState(true);

  useEffect(() => {
    const blinkTimer = setInterval(() => setBlink((b) => !b), 530);
    return () => clearInterval(blinkTimer);
  }, []);

  useEffect(() => {
    const current = typewriterPhrases[phraseIndex];
    let timeout;
    if (!deleting && charIndex < current.length) {
      timeout = setTimeout(() => {
        setDisplayed(current.slice(0, charIndex + 1));
        setCharIndex((i) => i + 1);
      }, 60);
    } else if (!deleting && charIndex === current.length) {
      timeout = setTimeout(() => setDeleting(true), 1800);
    } else if (deleting && charIndex > 0) {
      timeout = setTimeout(() => {
        setDisplayed(current.slice(0, charIndex - 1));
        setCharIndex((i) => i - 1);
      }, 35);
    } else if (deleting && charIndex === 0) {
      setDeleting(false);
      setPhraseIndex((i) => (i + 1) % typewriterPhrases.length);
    }
    return () => clearTimeout(timeout);
  }, [charIndex, deleting, phraseIndex]);

  const skills = [
    { label: "Python", color: "#3b82f6" },
    { label: "Data Analytics", color: "#8b5cf6" },
    { label: "Machine Learning", color: "#ec4899" },
    { label: "Cybersecurity", color: "#10b981" },
    { label: "SQL", color: "#f59e0b" },
    { label: "Vibe Coding", color: "#ef4444" },
  ];

  const interests = [
    { icon: "🤖", label: "AI & ML" },
    { icon: "🔐", label: "Cyber" },
    { icon: "🎨", label: "Arts" },
    { icon: "🧠", label: "Psychology" },
    { icon: "📊", label: "Data" },
    { icon: "💡", label: "Ideas" },
  ];

  return (
    <div
      style={{
        fontFamily: "'Courier New', monospace",
        background: "#0d1117",
        color: "#e6edf3",
        minHeight: "100vh",
        padding: "0",
        margin: "0",
        overflowX: "hidden",
      }}
    >
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;700;800&display=swap');
        * { box-sizing: border-box; }
        body { margin: 0; }
        .card { 
          background: #161b22; 
          border: 1px solid #30363d; 
          border-radius: 12px; 
          padding: 20px;
          transition: border-color 0.2s, transform 0.2s;
        }
        .card:hover { 
          border-color: #58a6ff; 
          transform: translateY(-2px);
        }
        .tag {
          display: inline-block;
          padding: 4px 12px;
          border-radius: 20px;
          font-size: 12px;
          font-family: 'Space Mono', monospace;
          font-weight: 700;
          letter-spacing: 0.05em;
          margin: 4px;
          transition: transform 0.15s;
        }
        .tag:hover { transform: scale(1.07); }
        .shake:hover { animation: wiggle 0.4s; }
        @keyframes wiggle {
          0%,100% { transform: rotate(0deg); }
          25% { transform: rotate(-4deg); }
          75% { transform: rotate(4deg); }
        }
        @keyframes float {
          0%, 100% { transform: translateY(0px); }
          50% { transform: translateY(-8px); }
        }
        @keyframes pulse-glow {
          0%, 100% { box-shadow: 0 0 0 0 rgba(88, 166, 255, 0.3); }
          50% { box-shadow: 0 0 20px 4px rgba(88, 166, 255, 0.15); }
        }
        .float-emoji { animation: float 3s ease-in-out infinite; display: inline-block; }
        .glow-border { animation: pulse-glow 3s ease-in-out infinite; }
        .divider { 
          border: none; 
          height: 1px; 
          background: linear-gradient(90deg, transparent, #30363d, transparent);
          margin: 24px 0;
        }
        a { color: #58a6ff; text-decoration: none; }
        a:hover { text-decoration: underline; }
        .noise-bg::before {
          content: '';
          position: absolute;
          inset: 0;
          background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
          pointer-events: none;
          border-radius: 12px;
        }
      `}</style>

      {/* Header Hero */}
      <div
        style={{
          position: "relative",
          background: "linear-gradient(135deg, #0d1117 0%, #161b22 50%, #0d1117 100%)",
          borderBottom: "1px solid #30363d",
          padding: "48px 32px 40px",
          textAlign: "center",
          overflow: "hidden",
        }}
      >
        {/* Decorative grid */}
        <div
          style={{
            position: "absolute",
            inset: 0,
            backgroundImage:
              "linear-gradient(rgba(88,166,255,0.04) 1px, transparent 1px), linear-gradient(90deg, rgba(88,166,255,0.04) 1px, transparent 1px)",
            backgroundSize: "40px 40px",
            pointerEvents: "none",
          }}
        />

        {/* Avatar placeholder */}
        <div
          className="glow-border"
          style={{
            width: 90,
            height: 90,
            borderRadius: "50%",
            background: "linear-gradient(135deg, #1f6feb, #8b5cf6)",
            margin: "0 auto 16px",
            display: "flex",
            alignItems: "center",
            justifyContent: "center",
            fontSize: 38,
            border: "3px solid #30363d",
            position: "relative",
            zIndex: 1,
          }}
        >
          ⚡
        </div>

        <h1
          style={{
            fontFamily: "'Syne', sans-serif",
            fontSize: "clamp(28px, 5vw, 44px)",
            fontWeight: 800,
            margin: "0 0 8px",
            background: "linear-gradient(90deg, #58a6ff, #bc8cff, #ff7b72)",
            WebkitBackgroundClip: "text",
            WebkitTextFillColor: "transparent",
            letterSpacing: "-0.02em",
            position: "relative",
            zIndex: 1,
          }}
        >
          Hey, I'm Ebuka 👋
        </h1>

        <div
          style={{
            fontFamily: "'Space Mono', monospace",
            fontSize: "clamp(13px, 2vw, 16px)",
            color: "#8b949e",
            minHeight: "24px",
            position: "relative",
            zIndex: 1,
          }}
        >
          <span style={{ color: "#58a6ff" }}>&gt;</span>{" "}
          <span style={{ color: "#e6edf3" }}>{displayed}</span>
          <span
            style={{
              opacity: blink ? 1 : 0,
              color: "#58a6ff",
              fontWeight: "bold",
              transition: "opacity 0.1s",
            }}
          >
            |
          </span>
        </div>
      </div>

      {/* Main content */}
      <div
        style={{
          maxWidth: 820,
          margin: "0 auto",
          padding: "32px 20px",
          display: "flex",
          flexDirection: "column",
          gap: "20px",
        }}
      >
        {/* About Me */}
        <div className="card" style={{ position: "relative" }}>
          <h2
            style={{
              fontFamily: "'Syne', sans-serif",
              fontWeight: 700,
              fontSize: 18,
              margin: "0 0 14px",
              color: "#58a6ff",
              display: "flex",
              alignItems: "center",
              gap: 8,
            }}
          >
            <span className="float-emoji">📖</span> About Me
          </h2>
          <p
            style={{
              fontFamily: "'Space Mono', monospace",
              fontSize: 13,
              lineHeight: 1.85,
              color: "#c9d1d9",
              margin: 0,
            }}
          >
            I'm an undergrad studying{" "}
            <span
              style={{
                background: "rgba(88,166,255,0.15)",
                color: "#58a6ff",
                padding: "1px 6px",
                borderRadius: 4,
              }}
            >
              Information Systems & Technology
            </span>
            , and my brain refuses to pick just one lane. Tech, arts, psychology — I want it
            all. 🤷‍♂️
            <br />
            <br />
            I'm caught between{" "}
            <span style={{ color: "#bc8cff" }}>Data Analytics / ML</span> and{" "}
            <span style={{ color: "#10b981" }}>Cybersecurity</span> (and yes, both are massive
            rabbit holes). While I figure that out, I've decided to just{" "}
            <span style={{ color: "#ff7b72", fontWeight: "bold" }}>start building things</span>{" "}
            — because ideas sitting in your head are just daydreams.
            <br />
            <br />
            Currently in my <span style={{ color: "#f0c040" }}>"vibe coding"</span> era 🎵 — shipping
            small projects, learning by doing, and enjoying the chaos.
          </p>
        </div>

        {/* Two column: Interests + Currently */}
        <div
          style={{
            display: "grid",
            gridTemplateColumns: "repeat(auto-fit, minmax(260px, 1fr))",
            gap: 20,
          }}
        >
          {/* Interests */}
          <div className="card">
            <h2
              style={{
                fontFamily: "'Syne', sans-serif",
                fontWeight: 700,
                fontSize: 18,
                margin: "0 0 16px",
                color: "#58a6ff",
                display: "flex",
                alignItems: "center",
                gap: 8,
              }}
            >
              <span className="float-emoji" style={{ animationDelay: "0.5s" }}>
                🎯
              </span>{" "}
              Interests
            </h2>
            <div style={{ display: "flex", flexWrap: "wrap", gap: 8 }}>
              {interests.map(({ icon, label }) => (
                <div
                  key={label}
                  className="shake"
                  style={{
                    background: "#21262d",
                    border: "1px solid #30363d",
                    borderRadius: 8,
                    padding: "8px 14px",
                    fontFamily: "'Space Mono', monospace",
                    fontSize: 12,
                    color: "#c9d1d9",
                    cursor: "default",
                    display: "flex",
                    alignItems: "center",
                    gap: 6,
                  }}
                >
                  {icon} {label}
                </div>
              ))}
            </div>
          </div>

          {/* Currently */}
          <div className="card">
            <h2
              style={{
                fontFamily: "'Syne', sans-serif",
                fontWeight: 700,
                fontSize: 18,
                margin: "0 0 16px",
                color: "#58a6ff",
                display: "flex",
                alignItems: "center",
                gap: 8,
              }}
            >
              <span className="float-emoji" style={{ animationDelay: "1s" }}>
                🔭
              </span>{" "}
              Right Now
            </h2>
            <ul
              style={{
                fontFamily: "'Space Mono', monospace",
                fontSize: 12,
                lineHeight: 2,
                color: "#c9d1d9",
                margin: 0,
                paddingLeft: 16,
              }}
            >
              <li>
                🧪 Experimenting with <span style={{ color: "#bc8cff" }}>vibe coding</span> projects
              </li>
              <li>
                📚 Exploring <span style={{ color: "#58a6ff" }}>Data Analytics & ML</span>
              </li>
              <li>
                🔐 Dipping toes into <span style={{ color: "#10b981" }}>Cybersecurity</span>
              </li>
              <li>
                💡 Turning shower thoughts into <span style={{ color: "#f0c040" }}>actual apps</span>
              </li>
              <li>
                🤝 Looking for a <span style={{ color: "#ff7b72" }}>mentor</span>!
              </li>
            </ul>
          </div>
        </div>

        {/* Skills / Stack */}
        <div className="card">
          <h2
            style={{
              fontFamily: "'Syne', sans-serif",
              fontWeight: 700,
              fontSize: 18,
              margin: "0 0 16px",
              color: "#58a6ff",
              display: "flex",
              alignItems: "center",
              gap: 8,
            }}
          >
            <span className="float-emoji" style={{ animationDelay: "1.5s" }}>
              🛠️
            </span>{" "}
            Skills & Things I'm Learning
          </h2>
          <div style={{ display: "flex", flexWrap: "wrap" }}>
            {skills.map(({ label, color }) => (
              <span
                key={label}
                className="tag"
                style={{
                  background: `${color}18`,
                  color: color,
                  border: `1px solid ${color}40`,
                  cursor: "default",
                }}
              >
                {label}
              </span>
            ))}
          </div>
        </div>

        {/* The confession box */}
        <div
          className="card"
          style={{
            background: "linear-gradient(135deg, #161b22, #1a1f2e)",
            borderColor: "#bc8cff40",
            position: "relative",
            overflow: "hidden",
          }}
        >
          <div
            style={{
              position: "absolute",
              top: -20,
              right: -20,
              fontSize: 80,
              opacity: 0.06,
              transform: "rotate(15deg)",
              pointerEvents: "none",
            }}
          >
            💭
          </div>
          <h2
            style={{
              fontFamily: "'Syne', sans-serif",
              fontWeight: 700,
              fontSize: 18,
              margin: "0 0 12px",
              color: "#bc8cff",
              display: "flex",
              alignItems: "center",
              gap: 8,
            }}
          >
            <span className="float-emoji" style={{ animationDelay: "2s" }}>
              😅
            </span>{" "}
            Real Talk
          </h2>
          <p
            style={{
              fontFamily: "'Space Mono', monospace",
              fontSize: 12,
              lineHeight: 1.9,
              color: "#8b949e",
              margin: 0,
              fontStyle: "italic",
            }}
          >
            "I get a lot of ideas. Like, a LOT. And I know the saying —{" "}
            <span style={{ color: "#bc8cff", fontStyle: "normal" }}>
              an idea is nothing without action
            </span>
            . So that's what I'm doing now — acting on them, one small project at a time. Some
            will be great, some will flop, and that's totally fine. The goal is to build, learn,
            and not die of analysis paralysis."
          </p>
        </div>

        {/* Connect */}
        <div
          className="card glow-border"
          style={{
            textAlign: "center",
            background: "linear-gradient(135deg, #161b22, #1a2030)",
            borderColor: "#58a6ff40",
          }}
        >
          <h2
            style={{
              fontFamily: "'Syne', sans-serif",
              fontWeight: 700,
              fontSize: 18,
              margin: "0 0 8px",
              color: "#58a6ff",
            }}
          >
            📬 Let's Connect
          </h2>
          <p
            style={{
              fontFamily: "'Space Mono', monospace",
              fontSize: 12,
              color: "#8b949e",
              margin: "0 0 16px",
              lineHeight: 1.8,
            }}
          >
            Got something helpful, fun, or a collab idea? A mentor willing to take a chance on a
            curious undergrad? I'm all ears!
          </p>
          
            href="mailto:m.faraday99@gmail.com"
            style={{
              display: "inline-block",
              background: "linear-gradient(135deg, #1f6feb, #8b5cf6)",
              color: "#fff",
              padding: "10px 28px",
              borderRadius: 8,
              fontFamily: "'Space Mono', monospace",
              fontWeight: 700,
              fontSize: 13,
              letterSpacing: "0.05em",
              textDecoration: "none",
              transition: "opacity 0.2s, transform 0.2s",
            }}
            onMouseEnter={(e) => {
              e.target.style.opacity = "0.85";
              e.target.style.transform = "scale(1.04)";
            }}
            onMouseLeave={(e) => {
              e.target.style.opacity = "1";
              e.target.style.transform = "scale(1)";
            }}
          >
            ✉️ m.faraday99@gmail.com
          </a>
          <p
            style={{
              fontFamily: "'Space Mono', monospace",
              fontSize: 11,
              color: "#484f58",
              marginTop: 16,
              marginBottom: 0,
            }}
          >
            // open to: mentorship · collaborations · helpful convos · anything fun
          </p>
        </div>

        {/* Footer */}
        <div
          style={{
            textAlign: "center",
            fontFamily: "'Space Mono', monospace",
            fontSize: 11,
            color: "#484f58",
            paddingBottom: 16,
          }}
        >
          <hr className="divider" />
          ⚡ powered by curiosity & caffeine · built with vibes · © Ebuka
        </div>
      </div>
    </div>
  );
}
