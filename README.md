import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import Header from './components/Header';
import Footer from './components/Footer';
import Home from './pages/Home';
import About from './pages/About';
import './App.css';

function App() {
  return (
    <Router>
      <Header />
      <main>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
        </Routes>
      </main>
      <Footer />
    </Router>
  );
}

export default App;
import { Link } from 'react-router-dom';
import './Header.css';

export default function Header() {
  return (
    <header className="header">
      <div className="logo">My Advanced Blog</div>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>
    </header>
  );
}
import BlogCard from '../components/BlogCard';

const blogData = [
  { title: "React for Beginners", summary: "A quick intro to React.", image: "https://via.placeholder.com/300" },
  { title: "Responsive Design", summary: "Making apps work on all screens.", image: "https://via.placeholder.com/300" },
];

export default function Home() {
  return (
    <section className="home">
      {blogData.map((post, i) => (
        <BlogCard key={i} post={post} />
      ))}
    </section>
  );
}
import './BlogCard.css';

export default function BlogCard({ post }) {
  return (
    <div className="blog-card">
      <img src={post.image} alt={post.title} />
      <h3>{post.title}</h3>
      <p>{post.summary}</p>
    </div>
  );
}
/* App.css */
main {
  padding: 20px;
}

@media (max-width: 768px) {
  main {
    padding: 10px;
  }
}

/* BlogCard.css */
.blog-card {
  background: white;
  padding: 1rem;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  margin-bottom: 20px;
}

.blog-card img {
  max-width: 100%;
  border-radius: 8px;
}
