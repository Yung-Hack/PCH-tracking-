# PCH-tracking-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PCH Package Tracking - G Man</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #f0f4f8 0%, #d9e2ec 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .tracking-container {
            background: #ffffff;
            border-radius: 24px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.08), 0 0 0 1px rgba(0, 0, 0, 0.02);
            max-width: 800px;
            width: 100%;
            overflow: hidden;
        }

        /* Header */
        .tracking-header {
            background: linear-gradient(135deg, #1a365d 0%, #2c5282 100%);
            color: white;
            padding: 32px;
            position: relative;
            overflow: hidden;
        }

        .tracking-header::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -20%;
            width: 300px;
            height: 300px;
            background: rgba(255, 255, 255, 0.03);
            border-radius: 50%;
        }

        .tracking-header h1 {
            font-size: 1.5rem;
            font-weight: 600;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .tracking-header .icon {
            width: 32px;
            height: 32px;
            background: rgba(255, 255, 255, 0.15);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .tracking-number {
            font-family: 'SF Mono', monospace;
            font-size: 0.95rem;
            opacity: 0.9;
            letter-spacing: 0.5px;
        }

        .sender-info {
            margin-top: 12px;
            padding-top: 12px;
            border-top: 1px solid rgba(255, 255, 255, 0.15);
            font-size: 0.875rem;
            opacity: 0.85;
        }

        .sender-info strong {
            opacity: 1;
            color: #fbbf24;
        }

        /* Status Badge */
        .status-section {
            padding: 24px 32px;
            background: #fffbeb;
            border-bottom: 1px solid #fef3c7;
            display: flex;
            align-items: center;
            gap: 16px;
        }

        .status-badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: #f59e0b;
            color: white;
            padding: 8px 16px;
            border-radius: 100px;
            font-weight: 600;
            font-size: 0.875rem;
            animation: pulse 2s infinite;
            flex-shrink: 0;
        }

        @keyframes pulse {
            0%, 100% { box-shadow: 0 0 0 0 rgba(245, 158, 11, 0.4); }
            50% { box-shadow: 0 0 0 8px rgba(245, 158, 11, 0); }
        }

        .status-badge .dot {
            width: 8px;
            height: 8px;
            background: white;
            border-radius: 50%;
            animation: blink 1.5s infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }

        .status-text {
            color: #92400e;
            font-size: 0.95rem;
        }

        .status-text strong {
            color: #78350f;
        }

        /* Alert Banner - Fee Required */
        .alert-banner {
            padding: 20px 32px;
            background: linear-gradient(135deg, #fef2f2 0%, #fee2e2 100%);
            border-bottom: 1px solid #fecaca;
            display: flex;
            align-items: flex-start;
            gap: 16px;
        }

        .alert-icon {
            width: 40px;
            height: 40px;
            background: #ef4444;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
        }

        .alert-icon svg {
            width: 20px;
            height: 20px;
            color: white;
        }

        .alert-content h3 {
            font-size: 1rem;
            font-weight: 600;
            color: #991b1b;
            margin-bottom: 6px;
        }

        .alert-content p {
            font-size: 0.875rem;
            color: #b91c1c;
            line-height: 1.6;
            margin-bottom: 12px;
        }

        .fee-box {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: white;
            border: 2px solid #fca5a5;
            border-radius: 10px;
            padding: 12px 20px;
            margin-top: 4px;
        }

        .fee-label {
            font-size: 0.8rem;
            color: #7f1d1d;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            font-weight: 600;
        }

        .fee-amount {
            font-size: 1.5rem;
            font-weight: 700;
            color: #dc2626;
        }

        .fee-note {
            font-size: 0.75rem;
            color: #991b1b;
            margin-top: 8px;
        }

        /* Discount Badge */
        .discount-badge {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            background: #dcfce7;
            color: #166534;
            padding: 6px 14px;
            border-radius: 100px;
            font-size: 0.8rem;
            font-weight: 600;
            margin-bottom: 10px;
            border: 1px solid #86efac;
        }

        .discount-badge svg {
            width: 14px;
            height: 14px;
        }

        .original-price {
            text-decoration: line-through;
            color: #9ca3af;
            font-size: 0.875rem;
            margin-left: 8px;
        }

        /* Recipient Info */
        .recipient-section {
            padding: 24px 32px;
            background: #f8fafc;
            border-bottom: 1px solid #e2e8f0;
        }

        .recipient-card {
            display: flex;
            align-items: flex-start;
            gap: 16px;
        }

        .recipient-avatar {
            width: 48px;
            height: 48px;
            background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: 700;
            font-size: 1.125rem;
            flex-shrink: 0;
        }

        .recipient-details h3 {
            font-size: 1rem;
            font-weight: 600;
            color: #1e293b;
            margin-bottom: 4px;
        }

        .recipient-details .address {
            font-size: 0.875rem;
            color: #475569;
            line-height: 1.6;
        }

        /* Timeline */
        .timeline-section {
            padding: 40px 32px;
        }

        .section-title {
            font-size: 1.125rem;
            font-weight: 600;
            color: #1a202c;
            margin-bottom: 32px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .timeline {
            position: relative;
            padding-left: 24px;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 11px;
            top: 0;
            bottom: 0;
            width: 2px;
            background: #e2e8f0;
        }

        .timeline-item {
            position: relative;
            padding-bottom: 32px;
            opacity: 0;
            transform: translateX(-20px);
            animation: slideIn 0.5s forwards;
        }

        .timeline-item:nth-child(1) { animation-delay: 0.1s; }
        .timeline-item:nth-child(2) { animation-delay: 0.2s; }
        .timeline-item:nth-child(3) { animation-delay: 0.3s; }
        .timeline-item:nth-child(4) { animation-delay: 0.4s; }
        .timeline-item:nth-child(5) { animation-delay: 0.5s; }

        @keyframes slideIn {
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .timeline-item:last-child {
            padding-bottom: 0;
        }

        .timeline-dot {
            position: absolute;
            left: -24px;
            top: 2px;
            width: 24px;
            height: 24px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1;
        }

        .timeline-item.completed .timeline-dot {
            background: #10b981;
            border: 3px solid #d1fae5;
        }

        .timeline-item.completed .timeline-dot::after {
            content: '✓';
            color: white;
            font-size: 12px;
            font-weight: bold;
        }

        .timeline-item.current .timeline-dot {
            background: #f59e0b;
            border: 3px solid #fef3c7;
            animation: pulse-dot 2s infinite;
        }

        .timeline-item.current .timeline-dot::after {
            content: '';
            width: 8px;
            height: 8px;
            background: white;
            border-radius: 50%;
        }

        @keyframes pulse-dot {
            0%, 100% { box-shadow: 0 0 0 0 rgba(245, 158, 11, 0.4); }
            50% { box-shadow: 0 0 0 6px rgba(245, 158, 11, 0); }
        }

        .timeline-item.pending .timeline-dot {
            background: #e2e8f0;
            border: 3px solid #f1f5f9;
        }

        .timeline-content {
            background: #f8fafc;
            border-radius: 12px;
            padding: 16px 20px;
            border: 1px solid #e2e8f0;
            transition: all 0.3s ease;
        }

        .timeline-item.current .timeline-content {
            background: #fffbeb;
            border-color: #fcd34d;
            box-shadow: 0 4px 12px rgba(245, 158, 11, 0.08);
        }

        .timeline-title {
            font-weight: 600;
            color: #1e293b;
            font-size: 0.95rem;
            margin-bottom: 4px;
        }

        .timeline-item.current .timeline-title {
            color: #92400e;
        }

        .timeline-time {
            font-size: 0.8rem;
            color: #64748b;
            margin-bottom: 4px;
        }

        .timeline-desc {
            font-size: 0.85rem;
            color: #475569;
            line-height: 1.5;
        }

        .timeline-item.current .timeline-desc {
            color: #b45309;
        }

        /* Facility Info Card */
        .facility-card {
            margin: 0 32px 32px;
            background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 100%);
            border: 1px solid #bae6fd;
            border-radius: 16px;
            padding: 24px;
            display: flex;
            gap: 20px;
            align-items: flex-start;
        }

        .facility-icon {
            width: 48px;
            height: 48px;
            background: #0ea5e9;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
        }

        .facility-icon svg {
            width: 24px;
            height: 24px;
            color: white;
        }

        .facility-details h3 {
            font-size: 1rem;
            font-weight: 600;
            color: #0c4a6e;
            margin-bottom: 4px;
        }

        .facility-details p {
            font-size: 0.875rem;
            color: #0369a1;
            line-height: 1.6;
        }

        .facility-meta {
            display: flex;
            gap: 16px;
            margin-top: 12px;
            flex-wrap: wrap;
        }

        .meta-tag {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            font-size: 0.8rem;
            color: #0284c7;
            background: rgba(255, 255, 255, 0.6);
            padding: 4px 12px;
            border-radius: 100px;
        }

        .held-duration {
            margin-top: 12px;
            padding: 12px;
            background: rgba(245, 158, 11, 0.1);
            border: 1px solid rgba(245, 158, 11, 0.2);
            border-radius: 8px;
            font-size: 0.875rem;
            color: #92400e;
            font-weight: 500;
        }

        .held-duration .days-count {
            font-size: 1.25rem;
            font-weight: 700;
            color: #d97706;
        }

        /* Action Section */
        .action-section {
            margin: 0 32px 32px;
            padding: 24px;
            background: linear-gradient(135deg, #f0fdf4 0%, #dcfce7 100%);
            border: 2px dashed #86efac;
            border-radius: 16px;
            text-align: center;
        }

        .action-section h3 {
            font-size: 1.125rem;
            font-weight: 600;
            color: #166534;
            margin-bottom: 8px;
        }

        .action-section p {
            font-size: 0.875rem;
            color: #15803d;
            margin-bottom: 16px;
        }

        .pay-btn {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            background: #16a34a;
            color: white;
            border: none;
            padding: 14px 32px;
            border-radius: 12px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
            box-shadow: 0 4px 12px rgba(22, 163, 74, 0.3);
        }

        .pay-btn:hover {
            background: #15803d;
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(22, 163, 74, 0.4);
        }

        .pay-btn:active {
            transform: translateY(0);
        }

        .secure-note {
            margin-top: 12px;
            font-size: 0.75rem;
            color: #22c55e;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }

        /* Footer */
        .tracking-footer {
            padding: 20px 32px;
            background: #f8fafc;
            border-top: 1px solid #e2e8f0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
        }

        .help-text {
            font-size: 0.875rem;
            color: #64748b;
        }

        .help-text a {
            color: #2563eb;
            text-decoration: none;
            font-weight: 500;
        }

        .help-text a:hover {
            text-decoration: underline;
        }

        .refresh-btn {
            background: #1e293b;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            font-size: 0.875rem;
            font-weight: 500;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: all 0.2s;
        }

        .refresh-btn:hover {
            background: #334155;
            transform: translateY(-1px);
        }

        .refresh-btn:active {
            transform: translateY(0);
        }

        /* Responsive */
        @media (max-width: 600px) {
            .tracking-header {
                padding: 24px;
            }

            .status-section {
                padding: 20px 24px;
                flex-direction: column;
                align-items: flex-start;
                gap: 12px;
            }

            .alert-banner {
                padding: 20px 24px;
                flex-direction: column;
            }

            .recipient-section {
                padding: 20px 24px;
            }

            .timeline-section {
                padding: 32px 24px;
            }

            .facility-card {
                margin: 0 24px 24px;
                flex-direction: column;
            }

            .action-section {
                margin: 0 24px 24px;
            }

            .tracking-footer {
                padding: 16px 24px;
                flex-direction: column;
                text-align: center;
            }
        }
    </style>
</head>
<body>
    <div class="tracking-container">
        <!-- Header -->
        <div class="tracking-header">
            <h1>
                <span class="icon">
                    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                        <rect x="2" y="7" width="20" height="14" rx="2" ry="2"></rect>
                        <path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"></path>
                    </svg>
                </span>
                PCH Package Tracking
            </h1>
            <div class="tracking-number">Tracking No: <strong>PCH-2026-8842-7791</strong></div>
            <div class="sender-info">Shipped by <strong>Publishers Clearing House (PCH)</strong></div>
        </div>

        <!-- Status Section -->
        <div class="status-section">
            <div class="status-badge">
                <span class="dot"></span>
                On Hold
            </div>
            <div class="status-text">
                Your package is currently <strong>on hold</strong> at our facility pending government clearance.
            </div>
        </div>

        <!-- Alert Banner - Fee Required -->
        <div class="alert-banner">
            <div class="alert-icon">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M10.29 3.86L1.82 18a2 2 0 0 0 1.71 3h16.94a2 2 0 0 0 1.71-3L13.71 3.86a2 2 0 0 0-3.42 0z"></path>
                    <line x1="12" y1="9" x2="12" y2="13"></line>
                    <line x1="12" y1="17" x2="12.01" y2="17"></line>
                </svg>
            </div>
            <div class="alert-content">
                <div class="discount-badge">
                    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <polyline points="20 6 9 17 4 12"></polyline>
                    </svg>
                    Voucher Applied — 40% Discount
                </div>
                <h3>Action Required — Government Approval Fee</h3>
                <p>Recipient <strong>G Man</strong> must pay the required government approval fee before this package can be released from our facility and continue to its destination.</p>
                <div class="fee-box">
                    <span class="fee-label">Amount Due</span>
                    <span class="fee-amount">$135.00 USD</span>
                    <span class="original-price">$225.00</span>
                </div>
                <p class="fee-note">A voucher discount of $90 has been applied. Original fee was $225.00. This fee covers customs processing and government regulatory approval for your shipment.</p>
            </div>
        </div>

        <!-- Recipient Info -->
        <div class="recipient-section">
            <div class="recipient-card">
                <div class="recipient-avatar">GM</div>
                <div class="recipient-details">
                    <h3>G Man</h3>
                    <div class="address">
                        980 Dilworth Dr<br>
                        Kelowna, BC V1V 1S6<br>
                        Canada
                    </div>
                </div>
            </div>
        </div>

        <!-- Timeline -->
        <div class="timeline-section">
            <div class="section-title">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#64748b" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <circle cx="12" cy="12" r="10"></circle>
                    <polyline points="12 6 12 12 16 14"></polyline>
                </svg>
                Shipment Progress
            </div>

            <div class="timeline">
                <!-- Step 1: Completed -->
                <div class="timeline-item completed">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-title">Order Placed</div>
                        <div class="timeline-time">April 15, 2026 at 10:00 AM (GMT-7)</div>
                        <div class="timeline-desc">Order received and payment confirmed successfully by PCH.</div>
                    </div>
                </div>

                <!-- Step 2: Completed -->
                <div class="timeline-item completed">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-title">Processing</div>
                        <div class="timeline-time">April 16, 2026 at 3:15 PM (GMT-7)</div>
                        <div class="timeline-desc">Items picked, packed, and labeled for shipment.</div>
                    </div>
                </div>

                <!-- Step 3: Current - On Hold at Facility -->
                <div class="timeline-item current">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-title">On Hold — Awaiting Fee Payment</div>
                        <div class="timeline-time">April 17, 2026 at 9:30 AM (GMT-7) — Current</div>
                        <div class="timeline-desc">Package is held at our Main Distribution Center. <strong>Government approval fee of $135.00 USD is required</strong> from recipient G Man before the package can be released and dispatched to Kelowna, BC. A voucher discount of $90 has been applied (original fee: $225.00).</div>
                    </div>
                </div>

                <!-- Step 4: Pending -->
                <div class="timeline-item pending">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-title">In Transit</div>
                        <div class="timeline-time">Pending — Fee payment required</div>
                        <div class="timeline-desc">Package will be dispatched to the delivery address in Kelowna, BC once the approval fee is cleared.</div>
                    </div>
                </div>

                <!-- Step 5: Pending -->
                <div class="timeline-item pending">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-title">Out for Delivery</div>
                        <div class="timeline-time">Pending</div>
                        <div class="timeline-desc">Package will be handed to the local courier for final delivery.</div>
                    </div>
                </div>

                <!-- Step 6: Pending -->
                <div class="timeline-item pending">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <div class="timeline-title">Delivered</div>
                        <div class="timeline-time">Pending</div>
                        <div class="timeline-desc">Package delivered to G Man at 980 Dilworth Dr, Kelowna, BC.</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Facility Info -->
        <div class="facility-card">
            <div class="facility-icon">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path>
                    <polyline points="9 22 9 12 15 12 15 22"></polyline>
                </svg>
            </div>
            <div class="facility-details">
                <h3>Main Distribution Center — Hold Facility</h3>
                <p>Your package has been held at our central facility since Friday, April 17, 2026 at 9:30 AM (GMT-7). It cannot be released until the government approval fee is paid by the recipient.</p>
                <div class="facility-meta">
                    <span class="meta-tag">
                        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                            <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
                            <circle cx="12" cy="10" r="3"></circle>
                        </svg>
                        Central Sorting & Hold Facility
                    </span>
                    <span class="meta-tag">
                        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                            <rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect>
                            <line x1="16" y1="2" x2="16" y2="6"></line>
                            <line x1="8" y1="2" x2="8" y2="6"></line>
                            <line x1="3" y1="10" x2="21" y2="10"></line>
                        </svg>
                        Held Since: Apr 17, 9:30 AM GMT-7
                    </span>
                </div>
                <div class="held-duration">
                    <span class="days-count">14</span> days on hold — awaiting $135.00 government approval fee payment (discounted from $225.00)
                </div>
            </div>
        </div>

        <!-- Action Section -->
        <div class="action-section">
            <h3>Complete Your Shipment</h3>
            <p>To release your package from hold and continue delivery to Kelowna, BC, please pay the discounted government approval fee below.</p>
            <button class="pay-btn" onclick="handlePayment()">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <rect x="1" y="4" width="22" height="16" rx="2" ry="2"></rect>
                    <line x1="1" y1="10" x2="23" y2="10"></line>
                </svg>
                Pay $135.00 Now
            </button>
            <div class="secure-note">
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                    <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
                </svg>
                Secure encrypted payment processing
            </div>
        </div>

        <!-- Footer -->
        <div class="tracking-footer">
            <div class="help-text">
                Need help? <a href="#">Contact PCH Support</a> or call <a href="tel:+18001234567">1-800-123-4567</a>
            </div>
            <button class="refresh-btn" onclick="refreshTracking()">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="23 4 23 10 17 10"></polyline>
                    <path d="M20.49 15a9 9 0 1 1-2.12-9.36L23 10"></path>
                </svg>
                Refresh Status
            </button>
        </div>
    </div>

    <script>
        function refreshTracking() {
            const btn = document.querySelector('.refresh-btn');
            const originalText = btn.innerHTML;
            
            btn.innerHTML = `
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="animation: spin 1s linear infinite;">
                    <line x1="12" y1="2" x2="12" y2="6"></line>
                    <line x1="12" y1="18" x2="12" y2="22"></line>
                    <line x1="4.93" y1="4.93" x2="7.76" y2="7.76"></line>
                    <line x1="16.24" y1="16.24" x2="19.07" y2="19.07"></line>
                    <line x1="2" y1="12" x2="6" y2="12"></line>
                    <line x1="18" y1="12" x2="22" y2="12"></line>
                    <line x1="4.93" y1="19.07" x2="7.76" y2="16.24"></line>
                    <line x1="16.24" y1="7.76" x2="19.07" y2="4.93"></line>
                </svg>
                Updating...
            `;
            btn.disabled = true;
            
            setTimeout(() => {
                btn.innerHTML = originalText;
                btn.disabled = false;
                
                showToast('Tracking status updated successfully!');
            }, 1500);
        }

        function handlePayment() {
            showToast('Redirecting to secure payment portal...');
        }

        function showToast(message) {
            const toast = document.createElement('div');
            toast.style.cssText = `
                position: fixed;
                bottom: 24px;
                left: 50%;
                transform: translateX(-50%);
                background: #1e293b;
                color: white;
                padding: 12px 24px;
                border-radius: 12px;
                font-size: 0.875rem;
                font-weight: 500;
                box-shadow: 0 10px 40px rgba(0,0,0,0.2);
                z-index: 1000;
                animation: toastIn 0.3s ease, toastOut 0.3s ease 2.5s forwards;
            `;
            toast.textContent = message;
            
            const style = document.createElement('style');
            style.textContent = `
                @keyframes toastIn { from { opacity: 0; transform: translateX(-50%) translateY(20px); } to { opacity: 1; transform: translateX(-50%) translateY(0); } }
                @keyframes toastOut { from { opacity: 1; transform: translateX(-50%) translateY(0); } to { opacity: 0; transform: translateX(-50%) translateY(20px); } }
                @keyframes spin { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
            `;
            document.head.appendChild(style);
            document.body.appendChild(toast);
            
            setTimeout(() => {
                toast.remove();
                style.remove();
            }, 3000);
        }
    </script>
</body>
</html>
