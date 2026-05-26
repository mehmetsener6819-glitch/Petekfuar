.<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Petek Fuar | Profesyonel Fuar Standı Tasarım & Uygulama</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Playfair+Display:wght@700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    
    <style>
        :root {
            --primary: #FFD700;
            --dark: #0f172a;
            --gray: #334155;
            --light: #f8fafc;
        }
        
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Inter', sans-serif;
            line-height: 1.7;
            color: #333;
            overflow-x: hidden;
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255,255,255,0.98);
            backdrop-filter: blur(12px);
            z-index: 1000;
            border-bottom: 1px solid #eee;
            transition: all 0.3s;
        }
        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 40px;
            height: 80px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            text-decoration: none;
            color: var(--dark);
        }
        .logo h1 {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            font-weight: 900;
        }
        nav a {
            margin-left: 32px;
            text-decoration: none;
            color: var(--gray);
            font-weight: 500;
            transition: color 0.3s;
        }
        nav a:hover { color: var(--dark); }

        /* Hero */
        #hero {
            height: 100vh;
            background: linear-gradient(rgba(15,23,42,0.85), rgba(15,23,42,0.9)), url('https://images.unsplash.com/photo-1581091226825-a6a9c4c6c8a0?ixlib=rb-4.0.3&auto=format&fit=crop&q=80') center/cover no-repeat;
            display: flex;
            align-items: center;
            color: white;
            position: relative;
        }
        .hero-content {
            max-width: 800px;
            padding: 0 40px;
        }
        .hero-content h1 {
            font-family: 'Playfair Display', serif;
            font-size: clamp(3rem, 8vw, 5.5rem);
            line-height: 1.1;
            margin-bottom: 20px;
        }
        .hero-content p {
            font-size: 1.25rem;
            margin-bottom: 40px;
            opacity: 0.9;
        }
        .btn {
            display: inline-block;
            padding: 16px 40px;
            border-radius: 50px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s;
        }
        .btn-primary {
            background: var(--primary);
            color: #0f172a;
        }
        .btn-primary:hover {
            transform: translateY(-4px);
            box-shadow: 0