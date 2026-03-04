# silly_stuff
Ví dụ main.jsx sẽ giống:

import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import "./styles/global.css";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

Bạn có thể giữ index.css và App.css, nhưng sau khi ok thì mình sẽ chỉ bạn cách dọn cho sạch.

4) Cài router

Mở terminal ở folder tornado-web chạy:

npm i react-router-dom
5) Thay src/App.jsx thành routing nhiều trang

Mở src/App.jsx → xóa hết → dán cái này:

import { BrowserRouter, Routes, Route, Navigate } from "react-router-dom";
import Header from "./components/Header";
import Footer from "./components/Footer";
import ProtectedRoute from "./components/ProtectedRoute";

import Home from "./pages/Home";
import About from "./pages/About";
import Solutions from "./pages/Solutions";
import Projects from "./pages/Projects";
import Pricing from "./pages/Pricing";
import Stats from "./pages/Stats";
import Contact from "./pages/Contact";
import AdminLogin from "./pages/AdminLogin";
import AdminDashboard from "./pages/AdminDashboard";

export default function App() {
  return (
    <BrowserRouter>
      <Header />
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/solutions" element={<Solutions />} />
        <Route path="/projects" element={<Projects />} />
        <Route path="/pricing" element={<Pricing />} />
        <Route path="/stats" element={<Stats />} />
        <Route path="/contact" element={<Contact />} />

        <Route path="/admin" element={<AdminLogin />} />
        <Route
          path="/admin/dashboard"
          element={
            <ProtectedRoute>
              <AdminDashboard />
            </ProtectedRoute>
          }
        />

        <Route path="*" element={<Navigate to="/" replace />} />
      </Routes>
      <Footer />
    </BrowserRouter>
  );
}
6) Tạo file “stub” trước để chạy không lỗi (rất quan trọng)

Trước khi copy code dài, bạn tạo nội dung tối thiểu cho từng file để React chạy.

src/components/ProtectedRoute.jsx
import { Navigate } from "react-router-dom";

export default function ProtectedRoute({ children }) {
  const token = localStorage.getItem("token");
  if (!token) return <Navigate to="/admin" replace />;
  return children;
}
src/components/Header.jsx
export default function Header() {
  return (
    <div style={{ padding: 12, borderBottom: "1px solid #e5e7eb" }}>
      Header (tạm) — sau đó mình sẽ paste bản full style
    </div>
  );
}
src/components/Footer.jsx
export default function Footer() {
  return (
    <div style={{ padding: 12, borderTop: "1px solid #e5e7eb" }}>
      Footer (tạm)
    </div>
  );
}
Các page tạm (ví dụ src/pages/Home.jsx)
export default function Home() {
  return <div className="container" style={{ padding: "40px 16px" }}>Home</div>;
}

Bạn làm tương tự cho About/Solutions/Projects/Pricing/Stats/Contact:

export default function About(){ return <div className="container" style={{padding:"40px 16px"}}>About</div>; }
Admin page tạm:

src/pages/AdminLogin.jsx

export default function AdminLogin() {
  return <div className="container" style={{ padding: "40px 16px" }}>Admin Login</div>;
}

src/pages/AdminDashboard.jsx

export default function AdminDashboard() {
  return <div className="container" style={{ padding: "40px 16px" }}>Admin Dashboard</div>;
}
