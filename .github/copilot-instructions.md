App name: Ben Fitness Gym

---

# **Best Practices for Expo Router (Universal App), NativeWind, and Firebase Firestore**

---

## for package manager

Use **pnpm** for package management. work well with Expo Router and React Native.

---

## 🧱 Project Stack Overview

| Tool             | Purpose                           |
| ---------------- | --------------------------------- |
| **Expo Router**  | File-based routing for mobile/web |
| **React Native** | Core framework                    |
| **NativeWind**   | Tailwind CSS for React Native     |
| **Firebase**     | Backend: Firestore, Auth, etc.    |

---

## 📁 Recommended Folder Structure (Expo Router)

```
app/                     # Screens using file-based routing
├── index.tsx            # Home screen
├── customer/
│   ├── index.tsx        # Customer list
│   └── [id].tsx         # Customer detail
components/              # Reusable presentational components
features/                # Logic grouped by domain (customer, income)
lib/                     # Firebase config, helpers, hooks
store/                   # Global state (e.g. Zustand)
styles/                  # NativeWind config, themes
assets/                  # Fonts, images, icons
hooks/                   # Custom hooks
utils/                  # Utility functions
types/                  # TypeScript types
interfaces/             # TypeScript interfaces
```

---

## 🔥 Firebase Firestore Best Practices

### Structure Example

```
/customers
  /<id>
    name: "Juan"
    type: "monthly"
    startDate
    endDate

/payments
  /<id>
    customerId
    amount
    type: "walkin" | "subscription"
    createdAt: serverTimestamp()
```

### Tips

- Use flat structures instead of deep nesting
- Use `serverTimestamp()` for time fields
- Enable **offline persistence**
- Create helper services (e.g. `addCustomer.ts`, `fetchPayments.ts`)

---

## 🎨 NativeWind Best Practices & Design System

### NativeWind Usage

- Use `className` for all styling needs
- Leverage Tailwind utilities for layout, spacing, colors, typography
- Create custom components using NativeWind classes
- Use conditional classes for interactive states

### 🎯 Design System Colors

Our app uses a custom color palette defined in `global.css`. Use these semantic colors:

```tsx
// Primary colors (gym branding - green theme)
className = 'bg-primary text-primary-foreground'; // Main brand color
className = 'bg-secondary text-secondary-foreground'; // Secondary actions
className = 'bg-accent text-accent-foreground'; // Highlights

// Status colors
className = 'bg-destructive text-destructive-foreground'; // Errors, deletions
className = 'text-muted-foreground'; // Disabled/secondary text

// Surface colors
className = 'bg-background text-foreground'; // Main background
className = 'bg-card text-card-foreground'; // Card backgrounds
className = 'border-border'; // Borders
```

### 📱 Layout Patterns

#### Screen Layout

```tsx
// Standard screen wrapper
<View className="flex-1 bg-background p-4">
    <Text className="text-2xl font-bold text-foreground mb-6">Screen Title</Text>
    {/* Content */}
</View>

// With safe area (for screens with status bar)
<View className="flex-1 bg-background pt-safe">
    <View className="p-4">
        {/* Content */}
    </View>
</View>
```

#### Card Components

```tsx
// Standard card
<View className="bg-card border border-border rounded-lg p-4 mb-4 shadow-sm">
    <Text className="text-lg font-semibold text-card-foreground">Card Title</Text>
    <Text className="text-muted-foreground mt-1">Card description</Text>
</View>

// Elevated card with more emphasis
<View className="bg-card border border-border rounded-lg p-6 mx-4 shadow-md">
    {/* Content */}
</View>
```

### 🔘 Button Styles

```tsx
// Primary button
<TouchableOpacity className="bg-primary px-6 py-3 rounded-lg active:bg-primary/90">
    <Text className="text-primary-foreground font-semibold text-center">Primary Action</Text>
</TouchableOpacity>

// Secondary button
<TouchableOpacity className="bg-secondary border border-border px-6 py-3 rounded-lg active:bg-secondary/90">
    <Text className="text-secondary-foreground font-medium text-center">Secondary</Text>
</TouchableOpacity>

// Destructive button
<TouchableOpacity className="bg-destructive px-6 py-3 rounded-lg active:bg-destructive/90">
    <Text className="text-destructive-foreground font-semibold text-center">Delete</Text>
</TouchableOpacity>

// Icon button
<TouchableOpacity className="bg-accent p-3 rounded-full active:bg-accent/80">
    {/* Icon component */}
</TouchableOpacity>
```

### 📝 Form Elements

```tsx
// Form container
<View className='bg-card border border-border rounded-lg p-4 space-y-4'>
    // Input field
    <View className='space-y-2'>
        <Text className='text-sm font-medium text-foreground'>Label</Text>
        <TextInput
            className='border border-border bg-input rounded-md px-3 py-3 text-foreground focus:border-ring'
            placeholder='Enter value'
            placeholderTextColor='hsl(var(--muted-foreground))'
        />
    </View>
    // Select/Picker wrapper
    <View className='space-y-2'>
        <Text className='text-sm font-medium text-foreground'>
            Select Option
        </Text>
        <View className='border border-border bg-input rounded-md'>
            {/* Picker component */}
        </View>
    </View>
</View>
```

### 📊 Data Display

```tsx
// Stats card
<View className="bg-card border border-border rounded-lg p-4">
    <Text className="text-2xl font-bold text-card-foreground">{value}</Text>
    <Text className="text-sm text-muted-foreground">{label}</Text>
</View>

// List item
<TouchableOpacity className="bg-card border-b border-border p-4 active:bg-accent">
    <View className="flex-row justify-between items-center">
        <View className="flex-1">
            <Text className="font-semibold text-card-foreground">{title}</Text>
            <Text className="text-sm text-muted-foreground mt-1">{subtitle}</Text>
        </View>
        <Text className="text-primary font-medium">{action}</Text>
    </View>
</TouchableOpacity>
```

### 🎨 Typography Scale

```tsx
// Headings
<Text className="text-3xl font-bold text-foreground">     // Main title
<Text className="text-2xl font-bold text-foreground">     // Section title
<Text className="text-xl font-semibold text-foreground">  // Subsection
<Text className="text-lg font-medium text-foreground">    // Card title

// Body text
<Text className="text-base text-foreground">              // Default text
<Text className="text-sm text-muted-foreground">          // Secondary text
<Text className="text-xs text-muted-foreground">          // Caption/metadata
```

### 📏 Spacing System

Use consistent spacing throughout the app:

```tsx
// Margins & Padding
className = 'p-4'; // Standard container padding
className = 'p-6'; // Larger container padding
className = 'py-3 px-6'; // Button padding
className = 'space-y-4'; // Vertical spacing between elements
className = 'gap-4'; // Flexbox gap

// Specific spacing
className = 'mt-6 mb-4'; // Section spacing
className = 'mx-4'; // Horizontal margins
```

### 🌙 Dark Mode Support

All colors automatically support dark mode via the CSS variables. Use semantic colors instead of hardcoded ones:

```tsx
// ✅ Good - uses semantic colors
className = 'bg-card text-card-foreground';

// ❌ Avoid - hardcoded colors don't adapt to dark mode
className = 'bg-white text-black';
```

### 📱 Responsive Design

```tsx
// Mobile-first responsive utilities
className = 'flex-col md:flex-row'; // Stack on mobile, row on larger screens
className = 'text-sm md:text-base'; // Smaller text on mobile
className = 'p-4 md:p-6'; // Less padding on mobile
```

### Example Components

```tsx
// Customer Card Component
<View className="bg-card border border-border rounded-lg p-4 mb-3 shadow-sm">
    <View className="flex-row justify-between items-start mb-2">
        <Text className="text-lg font-semibold text-card-foreground">{customer.name}</Text>
        <View className="bg-primary/10 px-2 py-1 rounded-full">
            <Text className="text-xs font-medium text-primary">{customer.type}</Text>
        </View>
    </View>
    <Text className="text-sm text-muted-foreground mb-3">
        Joined: {formatDate(customer.startDate)}
    </Text>
    <View className="flex-row gap-2">
        <TouchableOpacity className="flex-1 bg-primary py-2 rounded-md active:bg-primary/90">
            <Text className="text-primary-foreground font-medium text-center">View Details</Text>
        </TouchableOpacity>
        <TouchableOpacity className="bg-secondary border border-border py-2 px-4 rounded-md active:bg-secondary/90">
            <Text className="text-secondary-foreground font-medium">Edit</Text>
        </TouchableOpacity>
    </View>
</View>

// Income Summary Card
<View className="bg-card border border-border rounded-lg p-6 shadow-md">
    <Text className="text-xl font-bold text-card-foreground mb-4">Today's Income</Text>
    <View className="flex-row justify-between items-center mb-4">
        <View>
            <Text className="text-3xl font-bold text-primary">₱{todayIncome}</Text>
            <Text className="text-sm text-muted-foreground">Total collected</Text>
        </View>
        <View className="bg-primary/10 p-3 rounded-full">
            {/* Money icon */}
        </View>
    </View>
    <View className="flex-row justify-between pt-4 border-t border-border">
        <View>
            <Text className="text-lg font-semibold text-card-foreground">{walkInsCount}</Text>
            <Text className="text-xs text-muted-foreground">Walk-ins</Text>
        </View>
        <View>
            <Text className="text-lg font-semibold text-card-foreground">{subscriptionsCount}</Text>
            <Text className="text-xs text-muted-foreground">Subscriptions</Text>
        </View>
    </View>
</View>
```

### 🎯 Design Principles for Ben Fitness Gym

1. **Clean & Professional**: Use plenty of white space, clear typography
2. **Accessible**: High contrast, readable text sizes, touch-friendly buttons
3. **Consistent**: Use the design system colors and spacing consistently
4. **Mobile-First**: Design for mobile, enhance for larger screens
5. **Fast & Intuitive**: Quick actions, clear navigation, immediate feedback

---

## ⚛️ Component Guidelines

| When to Use           | Guideline                                                      |
| --------------------- | -------------------------------------------------------------- |
| **NativeWind**        | All styling needs (layout, colors, typography, spacing)        |
| **Custom components** | Screens, Cards, Reusable UI in `components/`                   |
| **Hooks**             | All logic in `features/` or `lib/` (e.g. `useCustomerForm.ts`) |

---

## 🔄 State Management

Use **Zustand** or **Context API**:

```ts
import { create } from 'zustand';

export const useCustomerStore = create((set) => ({
    customers: [],
    setCustomers: (data) => set({ customers: data }),
}));
```

---

## 🚦 Navigation (Expo Router)

- File-based routing (like Next.js)
- Use `<Link />` for in-app navigation
- Dynamic routes via `[id].tsx`

### Example:

```tsx
<Link href='/customer/123'>Go to Juan</Link>
```

---

## ⚙️ Best Practices Summary

| Area            | Best Practice                                                      |
| --------------- | ------------------------------------------------------------------ |
| **Routing**     | Use Expo Router structure, group screens by domain                 |
| **Styling**     | Use NativeWind for all styling needs                               |
| **UI**          | Componentize repetitive UI, keep screens clean                     |
| **State**       | Local state with `useState`, global state with Zustand             |
| **Firestore**   | Flat structure, batch writes, offline enabled                      |
| **Performance** | Use `FlatList`, memoize components, handle loading states properly |

---

Want help with:

- Example screen using NativeWind + Firebase?
- `tailwind.config.js` setup for React Native?
- Firebase emulator or deployment setup?

Let me know, I can scaffold it for you 🔧🔥

@/lib/firebase.ts

```
// Import the functions you need from the SDKs you need
import { getAnalytics } from 'firebase/analytics';
import { initializeApp } from 'firebase/app';
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
    apiKey: process.env.EXPO_PUBLIC_FIREBASE_WEB_API_KEY,
    authDomain: process.env.EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN,
    projectId: process.env.EXPO_PUBLIC_FIREBASE_PROJECT_ID,
    storageBucket: process.env.EXPO_PUBLIC_FIREBASE_STORAGE_BUCKET,
    messagingSenderId: process.env.EXPO_PUBLIC_FIREBASE_MESSAGING_SENDER_ID,
    appId: process.env.EXPO_PUBLIC_FIREBASE_APP_ID,
    measurementId: process.env.EXPO_PUBLIC_FIREBASE_MEASUREMENT_ID,
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const analytics = getAnalytics(app);
```

.env

```
Firebase configuration - these need to be public for client SDK
EXPO_PUBLIC_FIREBASE_WEB_API_KEY=AIzaSyAY7ll9lyk3y0HekOTuv_NT6628U810xw4
EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN=ben-fitness-gym.firebaseapp.com
EXPO_PUBLIC_FIREBASE_PROJECT_ID=ben-fitness-gym
EXPO_PUBLIC_FIREBASE_STORAGE_BUCKET=ben-fitness-gym.firebasestorage.app
EXPO_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=822542779642
EXPO_PUBLIC_FIREBASE_APP_ID=1:822542779642:web:0ed5f79fca0af0b3f93543
EXPO_PUBLIC_FIREBASE_MEASUREMENT_ID=G-7QF09GBDPG
```
