# iOS (Swift/SwiftUI) 구현

# RunConnect iOS 앱 구현

PRD와 디자인 가이드를 바탕으로 SwiftUI 기반의 RunConnect 앱을 구현하겠습니다.

## 1. 프로젝트 구조

```
RunConnect/
├── App/
│   ├── RunConnectApp.swift
│   └── ContentView.swift
├── Core/
│   ├── Constants/
│   │   ├── Colors.swift
│   │   ├── Typography.swift
│   │   └── Layout.swift
│   ├── Extensions/
│   │   ├── Color+Extension.swift
│   │   ├── View+Extension.swift
│   │   └── Double+Extension.swift
│   └── Utils/
│       ├── LocationManager.swift
│       ├── HapticManager.swift
│       └── NetworkManager.swift
├── Features/
│   ├── Authentication/
│   │   ├── Views/
│   │   ├── ViewModels/
│   │   └── Models/
│   ├── Home/
│   │   ├── Views/
│   │   ├── ViewModels/
│   │   └── Models/
│   ├── Running/
│   │   ├── Views/
│   │   ├── ViewModels/
│   │   └── Models/
│   ├── Matching/
│   │   ├── Views/
│   │   ├── ViewModels/
│   │   └── Models/
│   └── Profile/
│       ├── Views/
│       ├── ViewModels/
│       └── Models/
└── Resources/
    ├── Assets.xcassets
    └── Info.plist
```

## 2. 핵심 파일들

### 2.1 앱 진입점

```swift
// RunConnectApp.swift
import SwiftUI
import Firebase

@main
struct RunConnectApp: App {
    @StateObject private var authViewModel = AuthenticationViewModel()
    @StateObject private var locationManager = LocationManager()
    
    init() {
        FirebaseApp.configure()
        setupAppearance()
    }
    
    var body: some Scene {
        WindowGroup {
            ContentView()
                .environmentObject(authViewModel)
                .environmentObject(locationManager)
                .onAppear {
                    authViewModel.checkAuthenticationState()
                }
        }
    }
    
    private func setupAppearance() {
        // Navigation Bar 스타일 설정
        let appearance = UINavigationBarAppearance()
        appearance.configureWithOpaqueBackground()
        appearance.backgroundColor = UIColor(AppColors.background)
        appearance.titleTextAttributes = [
            .foregroundColor: UIColor(AppColors.textPrimary),
            .font: UIFont.systemFont(ofSize: 20, weight: .semibold)
        ]
        
        UINavigationBar.appearance().standardAppearance = appearance
        UINavigationBar.appearance().scrollEdgeAppearance = appearance
    }
}
```

### 2.2 메인 컨텐츠 뷰

```swift
// ContentView.swift
import SwiftUI

struct ContentView: View {
    @EnvironmentObject var authViewModel: AuthenticationViewModel
    @StateObject private var tabViewModel = TabViewModel()
    
    var body: some View {
        Group {
            if authViewModel.isAuthenticated {
                MainTabView()
                    .environmentObject(tabViewModel)
            } else {
                OnboardingView()
            }
        }
        .animation(.easeInOut(duration: 0.3), value: authViewModel.isAuthenticated)
    }
}
```

## 3. 디자인 시스템

### 3.1 컬러 정의

```swift
// Colors.swift
import SwiftUI

struct AppColors {
    // Main Colors
    static let primary = Color(hex: "#FF6B35")
    static let secondary = Color(hex: "#2E86AB")
    static let accent = Color(hex: "#F18F01")
    
    // Support Colors
    static let background = Color(hex: "#FAFBFC")
    static let surface = Color(hex: "#FFFFFF")
    static let textPrimary = Color(hex: "#1A1D23")
    static let textSecondary = Color(hex: "#6B7280")
    static let success = Color(hex: "#10B981")
    static let warning = Color(hex: "#F59E0B")
    static let error = Color(hex: "#EF4444")
    
    // UI Elements
    static let cardShadow = Color.black.opacity(0.06)
    static let border = Color(hex: "#E5E7EB")
}

// Color+Extension.swift
import SwiftUI

extension Color {
    init(hex: String) {
        let hex = hex.trimmingCharacters(in: CharacterSet.alphanumerics.inverted)
        var int: UInt64 = 0
        Scanner(string: hex).scanHexInt64(&int)
        let a, r, g, b: UInt64
        switch hex.count {
        case 3: // RGB (12-bit)
            (a, r, g, b) = (255, (int >> 8) * 17, (int >> 4 & 0xF) * 17, (int & 0xF) * 17)
        case 6: // RGB (24-bit)
            (a, r, g, b) = (255, int >> 16, int >> 8 & 0xFF, int & 0xFF)
        case 8: // ARGB (32-bit)
            (a, r, g, b) = (int >> 24, int >> 16 & 0xFF, int >> 8 & 0xFF, int & 0xFF)
        default:
            (a, r, g, b) = (1, 1, 1, 0)
        }
        
        self.init(
            .sRGB,
            red: Double(r) / 255,
            green: Double(g) / 255,
            blue: Double(b) / 255,
            opacity: Double(a) / 255
        )
    }
}
```

### 3.2 타이포그래피

```swift
// Typography.swift
import SwiftUI

struct AppTypography {
    // 헤더
    static let h1 = Font.system(size: 28, weight: .bold, design: .default)
    static let h2 = Font.system(size: 24, weight: .semibold, design: .default)
    static let h3 = Font.system(size: 20, weight: .semibold, design: .default)
    
    // 바디
    static let bodyLarge = Font.system(size: 18, weight: .regular, design: .default)
    static let bodyMedium = Font.system(size: 16, weight: .regular, design: .default)
    static let bodySmall = Font.system(size: 14, weight: .regular, design: .default)
    
    // 특수
    static let caption = Font.system(size: 12, weight: .medium, design: .default)
    static let numberDisplay = Font.system(size: 32, weight: .bold, design: .monospaced)
    static let timerDisplay = Font.system(size: 48, weight: .bold, design: .monospaced)
}
```

### 3.3 레이아웃 상수

```swift
// Layout.swift
import SwiftUI

struct AppLayout {
    // Spacing
    static let spacing: CGFloat = 8
    static let spacingSmall: CGFloat = 4
    static let spacingMedium: CGFloat = 12
    static let spacingLarge: CGFloat = 20
    static let spacingXLarge: CGFloat = 32
    
    // Padding
    static let paddingSmall: CGFloat = 8
    static let paddingMedium: CGFloat = 16
    static let paddingLarge: CGFloat = 20
    
    // Corner Radius
    static let cornerRadiusSmall: CGFloat = 8
    static let cornerRadiusMedium: CGFloat = 12
    static let cornerRadiusLarge: CGFloat = 16
    static let cornerRadiusButton: CGFloat = 28
    
    // Button Heights
    static let buttonHeightPrimary: CGFloat = 56
    static let buttonHeightSecondary: CGFloat = 44
    
    // Card
    static let cardPadding: CGFloat = 20
    static let cardSpacing: CGFloat = 12
}
```

## 4. 공통 컴포넌트

### 4.1 버튼 컴포넌트

```swift
// PrimaryButton.swift
import SwiftUI

struct PrimaryButton: View {
    let title: String
    let action: () -> Void
    var isLoading: Bool = false
    var isDisabled: Bool = false
    
    var body: some View {
        Button(action: action) {
            HStack {
                if isLoading {
                    ProgressView()
                        .progressViewStyle(CircularProgressViewStyle(tint: .white))
                        .scaleEffect(0.8)
                } else {
                    Text(title)
                        .font(AppTypography.bodyLarge)
                        .fontWeight(.semibold)
                }
            }
            .foregroundColor(.white)
            .frame(maxWidth: .infinity)
            .frame(height: AppLayout.buttonHeightPrimary)
            .background(
                RoundedRectangle(cornerRadius: AppLayout.cornerRadiusButton)
                    .fill(isDisabled ? AppColors.textSecondary : AppColors.primary)
            )
            .shadow(
                color: isDisabled ? .clear : AppColors.primary.opacity(0.3),
                radius: 6,
                x: 0,
                y: 4
            )
        }
        .disabled(isDisabled || isLoading)
        .scaleEffect(isDisabled ? 0.95 : 1.0)
        .animation(.easeInOut(duration: 0.2), value: isDisabled)
    }
}

// SecondaryButton.swift
struct SecondaryButton: View {
    let title: String
    let action: () -> Void
    var isDisabled: Bool = false
    
    var body: some View {
        Button(action: action) {
            Text(title)
                .font(AppTypography.bodyLarge)
                .fontWeight(.semibold)
                .foregroundColor(AppColors.primary)
                .frame(maxWidth: .infinity)
                .frame(height: AppLayout.buttonHeightPrimary)
                .background(
                    RoundedRectangle(cornerRadius: AppLayout.cornerRadiusButton)
                        .stroke(AppColors.primary, lineWidth: 2)
                        .background(
                            RoundedRectangle(cornerRadius: AppLayout.cornerRadiusButton)
                                .fill(AppColors.surface)
                        )
                )
        }
        .disabled(isDisabled)
        .opacity(isDisabled ? 0.6 : 1.0)
    }
}
```

### 4.2 카드 컴포넌트

```swift
// StatCard.swift
import SwiftUI

struct StatCard: View {
    let title: String
    let value: String
    let subtitle: String?
    var accentColor: Color = AppColors.primary
    
    var body: some View {
        VStack(alignment: .leading, spacing: AppLayout.spacingSmall) {
            HStack {
                Text(title)
                    .font(AppTypography.caption)
                    .foregroundColor(AppColors.textSecondary)
                    .textCase(.uppercase)
                
                Spacer()
            }
            
            Text(value)
                .font(AppTypography.numberDisplay)
                .foregroundColor(AppColors.textPrimary)
            
            if let subtitle = subtitle {
                Text(subtitle)
                    .font(AppTypography.bodySmall)
                    .foregroundColor(AppColors.textSecondary)
            }
        }
        .padding(AppLayout.paddingMedium)
        .frame(maxWidth: .infinity, alignment: .leading)
        .background(
            RoundedRectangle(cornerRadius: AppLayout.cornerRadiusMedium)
                .fill(AppColors.surface)
                .overlay(
                    RoundedRectangle(cornerRadius: AppLayout.cornerRadiusMedium)
                        .stroke(accentColor, lineWidth: 1)
                        .opacity(0.2)
                )
        )
        .overlay(
            RoundedRectangle(cornerRadius: AppLayout.cornerRadiusMedium)
                .stroke(accentColor, lineWidth: 4)
                .opacity(0.8),
            alignment: .leading
        )
        .shadow(color: AppColors.cardShadow, radius: 2, x: 0, y: 1)
    }
}
```

## 5. 홈 화면

### 5.1 홈 뷰모델

```swift
// HomeViewModel.swift
import Foundation
import Combine

@MainActor
class HomeViewModel: ObservableObject {
    @Published var weeklyStats = WeeklyStats()
    @Published var recentRuns: [RunRecord] = []
    @Published var isLoading = false
    @Published var errorMessage: String?
    
    private let runningRepository: RunningRepository
    private var cancellables = Set<AnyCancellable>()
    
    init(runningRepository: RunningRepository = RunningRepository()) {
        self.runningRepository = runningRepository
        loadData()
    }
    
    func loadData() {
        isLoading = true
        
        Task {
            do {
                async let weeklyStats = runningRepository.getWeeklyStats()
                async let recentRuns = runningRepository.getRecentRuns(limit: 3)
                
                self.weeklyStats = try await weeklyStats
                self.recentRuns = try await recentRuns
                
                isLoading = false
            } catch {
                errorMessage = error.localizedDescription
                isLoading = false
            }
        }
    }
    
    func refreshData() {
        loadData()
    }
}
```

### 5.2 홈 뷰

```swift
// HomeView.swift
import SwiftUI

struct HomeView: View {
    @StateObject private var viewModel = HomeViewModel()
    @EnvironmentObject var authViewModel: AuthenticationViewModel
    @State private var showingRunModeSelection = false
    
    var body: some View {
        NavigationView {
            ScrollView {
                LazyVStack(spacing: AppLayout.spacingLarge) {
                    // 헤더
                    headerView
                    
                    // 주간 통계
                    weeklyStatsView
                    
                    // 런닝 모드 선택 버튼들
                    runningModeButtons
                    
                    // 최근 런닝 기록
                    recentRunsView
                    
                    // 광고 배너 (하단)
                    AdBannerView()
                        .frame(height: 60)
                        .padding(.horizontal, AppLayout.paddingMedium)
                }
                .padding(.top, AppLayout.paddingSmall)
            }
            .background(AppColors.background)
            .navigationBarHidden(true)
            .refreshable {
                viewModel.refreshData()
            }
        }
        .sheet(isPresented: $showingRunModeSelection) {
            RunModeSelectionView()
        }
        .onAppear {
            viewModel.refreshData()
        }
    }
    
    private var headerView: some View {
        HStack {
            VStack(alignment: .leading, spacing: 4) {
                Text("안녕하세요")
                    .font(AppTypography.bodyMedium)
                    .foregroundColor(AppColors.textSecondary)
                
                Text(authViewModel.user?.displayName ?? "러너")
                    .font(AppTypography.h2)
                    .foregroundColor(AppColors.textPrimary)
            }
            
            Spacer()
            
            Button(action: {
                // 알림 화면 이동
            }) {
                Image(systemName: "bell")
                    .font(.title2)
                    .foregroundColor(AppColors.textSecondary)
            }
            
            Button(action: {
                // 프로필 화면 이동
            }) {
                AsyncImage(url: authViewModel.user?.profileImageURL) { image in
                    image
                        .resizable()
                        .aspectRatio(contentMode: .fill)
                } placeholder: {
                    Circle()
                        .fill(AppColors.primary.opacity(0.2))
                        .overlay(
                            Text(String(authViewModel.user?.displayName?.first ?? "U"))
                                .font(AppTypography.h3)
                                .foregroundColor(AppColors.primary)
                        )
                }
                .frame(width: 40, height: 40)
                .clipShape(Circle())
            }
        }
        .padding(.horizontal, AppLayout.paddingLarge)
    }
    
    private var weeklyStatsView: some View {
        VStack(alignment: .leading, spacing: AppLayout.spacingMedium) {
            Text("이번 주 런닝")
                .font(AppTypography.h3)
                .foregroundColor(AppColors.textPrimary)
                .padding(.horizontal, AppLayout.paddingLarge)
            
            HStack(spacing: AppLayout.spacingMedium) {
                StatCard(
                    title: "총 거리",
                    value: String(format: "%.1f", viewModel.weeklyStats.totalDistance),
                    subtitle: "km",
                    accentColor: AppColors.primary
                )
                
                StatCard(
                    title: "총 시간",
                    value: viewModel.weeklyStats.totalTimeFormatted,
                    subtitle: "시간",
                    accentColor: AppColors.secondary
                )
                
                StatCard(
                    title: "칼로리",
                    value: "\(viewModel.weeklyStats.totalCalories)",
                    subtitle: "kcal",
                    accentColor: AppColors.accent
                )
            }
            .padding(.horizontal, AppLayout.paddingLarge)
        }
    }
    
    private var runningModeButtons: some View {
        VStack(spacing: AppLayout.spacingMedium) {
            // 솔로 런닝 버튼
            RunModeCard(
                title: "솔로 런닝",
                subtitle: "나만의 페이스로 런닝하기",
                icon: "figure.walk",
                color: AppColors.primary,
                action: {
                    // 솔로 런닝 시작
                }
            )
            
            // 매칭 런닝 버튼
            RunModeCard(
                title: "매칭 런닝",
                subtitle: "다른 러너와 함께 런닝하기",
                icon: "person.2.fill",
                color: AppColors.secondary,
                action: {
                    // 매칭 런닝 시작
                    showingRunModeSelection = true
                }
            )
        }
        .padding(.horizontal, AppLayout.paddingLarge)
    }
    
    private var recentRunsView: some View {
        VStack(alignment: .leading, spacing: AppLayout.spacingMedium) {
            HStack {
                Text("최근 런닝")
                    .font(AppTypography.h3)
                    .foregroundColor(AppColors.textPrimary)
                
                Spacer()
                
                NavigationLink("전체보기") {
                    RunHistoryView()
                }
                .font(AppTypography.bodySmall)
                .foregroundColor(AppColors.primary)
            }
            .padding(.horizontal, AppLayout.paddingLarge)
            
            if viewModel.recentRuns.isEmpty {
                EmptyStateView(
                    title: "런닝 기록이 없습니다",
                    subtitle: "첫 런닝을 시작해보세요!",
                    icon: "figure.walk"
                )
                .padding(.horizontal, AppLayout.paddingLarge)
            } else {
                LazyVStack(spacing: AppLayout.spacingSmall) {
                    ForEach(viewModel.recentRuns) { run in
                        RunRecordCard(run: run)
                    }
                }
                .padding(.horizontal, AppLayout.paddingLarge)
            }
        }
    }
}

// RunModeCard.swift
struct RunModeCard: View {
    let title: String
    let subtitle: String
    let icon: String
    let color: Color
    let action: () -> Void
    
    var body: some View {
        Button(action: action) {
            HStack(spacing: AppLayout.spacingMedium) {
                // 아이콘
                Image(systemName: icon)
                    .font(.title)
                    .foregroundColor(color)
                    .frame(width: 50, height: 50)
                    .background(
                        Circle()
                            .fill(color.opacity(0.1))
                    )
                
                // 텍스트
                VStack(alignment: .leading, spacing: 4) {
                    Text(title)
                        .font(AppTypography.h3)
                        .foregroundColor(AppColors.textPrimary)
                    
                    Text(subtitle)
                        .font(AppTypography.bodySmall)
                        .foregroundColor(AppColors.textSecondary)
                }
                
                Spacer()
                
                // 화살표
                Image(systemName: "chevron.right")
                    .font(.title2)
                    .foregroundColor(AppColors.textSecondary)
            }
            .padding(AppLayout.paddingLarge)
            .background(
                RoundedRectangle(cornerRadius: AppLayout.cornerRadiusLarge)
                    .fill(AppColors.surface)
                    .shadow(color: AppColors.cardShadow, radius: 4, x: 0, y: 2)
            )
        }
        .buttonStyle(PlainButtonStyle())
    }
}
```

## 6. 런닝 추적 화면

### 6.1 런닝 뷰모델

```swift
// RunningViewModel.swift
import Foundation
import Combine
import CoreLocation

@MainActor
class RunningViewModel: ObservableObject {
    @Published var runningState: RunningState = .idle
    @Published var currentRun: RunSession?
    @Published var elapsedTime: TimeInterval = 0
    @Published var distance: Double = 0
    @Published var currentPace: Double = 0
    @Published var averagePace: Double = 0
    @Published var calories: Int = 0
    @Published var locations: [CLLocation] = []
    
    private let locationManager: LocationManager
    private let runningRepository: RunningRepository
    private var timer: Timer?
    private var startTime: Date?
    private var cancellables = Set<AnyCancellable>()
    
    enum RunningState {
        case idle, running, paused, completed
    }
    
    init(locationManager: LocationManager, runningRepository: RunningRepository = RunningRepository()) {
        self.locationManager = locationManager
        self.runningRepository = runningRepository
        
        setupLocationUpdates()
    }
    
    private func setupLocationUpdates() {
        locationManager.$location
            .compactMap { $0 }
            .sink { [weak self] location in
                self?.updateLocation(location)
            }
            .store(in: &cancellables)
    }
    
    func startRunning() {
        guard runningState == .idle else { return }
        
        runningState = .running
        startTime = Date()
        currentRun = RunSession(startTime: startTime!)
        
        locationManager.requestLocationPermission()
        locationManager.startTracking()
        
        startTimer()
        HapticManager.impact(.medium)
    }
    
    func pauseRunning() {
        guard runningState == .running else { return }
        
        runningState = .paused
        stopTimer()
        locationManager.stopTracking()
        HapticManager.impact(.light)
    }
    
    func resumeRunning() {
        guard runningState == .paused else { return }
        
        runningState = .running
        startTimer()
        locationManager.startTracking()
        HapticManager.impact(.medium)
    }
    
    func stopRunning() {
        runningState = .completed
        stopTimer()
        locationManager.stopTracking()
        
        // 런닝 데이터 저장
        saveRunningData()
        HapticManager.notification(.success)
    }
    
    private func startTimer() {
        timer = Timer.scheduledTimer(withTimeInterval: 1.0, repeats: true) { [weak self] _ in
            self?.updateElapsedTime()
        }
    }
    
    private func stopTimer() {
        timer?.invalidate()
        timer = nil
    }
    
    private func updateElapsedTime() {
        guard let startTime = startTime else { return }
        elapsedTime = Date().timeIntervalSince(startTime)
        updatePaceAndCalories()
    }
    
    private func updateLocation(_ location: CLLocation) {
        guard runningState == .running else { return }
        
        locations.append(location)
        
        // 거리 계산
        if locations.count > 1 {
            let previousLocation = locations[locations.count - 2]
            let distanceInterval = location.distance(from: previousLocation)
            distance += distanceInterval / 1000 // km로 변환
        }
        
        updatePaceAndCalories()
    }
    
    private func updatePaceAndCalories() {
        // 평균 페이스 계산 (분/km)
        if distance > 0 && elapsedTime > 0 {
            averagePace = (elapsedTime / 60) / distance
        }
        
        // 현재 페이스 계산 (최근 1km 기준)
        calculateCurrentPace()
        
        // 칼로리 계산 (간단한 공식 사용)
        calories = Int(distance * 60) // 1km당 약 60kcal로 가정
    }
    
    private func calculateCurrentPace() {
        // 최근 1km 또는 최근 5분간의 페이스 계산
        guard locations.count > 10 else { return }
        
        let recentLocations = Array(locations.suffix(10))
        let timeInterval = recentLocations.last!.timestamp.timeIntervalSince(recentLocations.first!.timestamp)
        let distanceInterval = calculateDistance(for: recentLocations)
        
        if distanceInterval > 0 {
            currentPace = (timeInterval / 60) / (distanceInterval / 1000)
        }
    }
    
    private func calculateDistance(for locations: [CLLocation]) -> Double {
        var totalDistance: Double = 0
        
        for i in 1..<locations.count {
            totalDistance += locations[i].distance(from: locations[i-1])
        }
        
        return totalDistance
    }
    
    private func saveRunningData() {
        guard let currentRun = currentRun else { return }
        
        let runRecord = RunRecord(
            id: UUID(),
            startTime: currentRun.startTime,
            endTime: Date(),
            distance: distance,
            duration: elapsedTime,
            averagePace: averagePace,
            calories: calories,
            locations: locations.map { RunLocation(from: $0) }
        )
        
        Task {
            do {
                try await runningRepository.saveRun(runRecord)
            } catch {
                print("Failed to save run: \(error)")
            }
        }
    }
    
    func reset() {
        runningState = .idle
        currentRun = nil
        elapsedTime = 0
        distance = 0
        currentPace = 0
        averagePace = 0
        calories = 0
        locations.removeAll()
        startTime = nil
        stopTimer()
    }
}
```

### 6.2 런닝 추적 뷰

```swift
// RunningTrackingView.swift
import SwiftUI
import MapKit

struct RunningTrackingView: View {
    @StateObject private var viewModel: RunningViewModel
    @EnvironmentObject private var locationManager: LocationManager
    @Environment(\.dismiss) private var dismiss
    @State private var region = MKCoordinateRegion(
        center: CLLocationCoordinate2D(latitude: 37.5665, longitude: 126.9780),
        span: MKCoordinateSpan(latitudeDelta: 0.01, longitudeDelta: 0.01)
    )
    @State private var showingStopAlert = false
    
    init() {
        _viewModel = StateObject(wrappedValue: RunningViewModel(locationManager: LocationManager.shared))
    }
    
    var body: some View {
        ZStack {
            // 배경 지도
            MapView(
                region: $region,
                locations: viewModel.locations,
                showsUserLocation: true
            )
            .ignoresSafeArea()
            
            // 오버레이 UI
            VStack {
                // 상단 상태바
                topStatusBar
                
                Spacer()
                
                // 중앙 런닝 데이터
                runningDataOverlay
                
                Spacer()
                
                // 하단 컨트롤 버튼들
                bottomControls
            }
        }
        .navigationBarHidden(true)
        .preferredColorScheme(.dark) // 런닝 중에는 다크모드
        .onAppear {
            updateRegionWithCurrentLocation()
        }
        .alert("런닝 종료", isPresented: $showingStopAlert) {
            Button("계속하기", role: .cancel) { }
            Button("종료하기", role: .destructive) {
                viewModel.stopRunning()
                dismiss()
            }
        } message: {
            Text("런닝을 종료하시겠습니까? 현재까지의 기록이 저장됩니다.")
        }
    }
    
    private var topStatusBar: some View {
        HStack {
            // GPS 신호 상태
            HStack(spacing: 4) {
                Circle()
                    .fill(locationManager.authorizationStatus == .authorizedWhenInU