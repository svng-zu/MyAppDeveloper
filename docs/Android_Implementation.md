# Android (Kotlin/Compose) 구현

# RunConnect - 런닝 앱 Android 구현

PRD와 디자인 가이드를 바탕으로 Phase 1 MVP 기준으로 전체 프로젝트 구조와 핵심 코드를 작성해드리겠습니다.

## 1. 프로젝트 구조

```
app/
├── src/main/java/com/runconnect/
│   ├── di/                     # Dependency Injection
│   ├── data/                   # Data Layer
│   │   ├── local/             # Room Database
│   │   ├── remote/            # Network APIs
│   │   └── repository/        # Repository Implementation
│   ├── domain/                # Domain Layer
│   │   ├── model/             # Domain Models
│   │   ├── repository/        # Repository Interfaces
│   │   └── usecase/           # Use Cases
│   ├── presentation/          # Presentation Layer
│   │   ├── ui/                # Compose UI Screens
│   │   ├── viewmodel/         # ViewModels
│   │   └── navigation/        # Navigation
│   ├── utils/                 # Utilities
│   └── MainActivity.kt
├── build.gradle.kts
└── proguard-rules.pro
```

## 2. 의존성 설정 (build.gradle.kts)

```kotlin
plugins {
    id("com.android.application")
    id("org.jetbrains.kotlin.android")
    id("kotlin-kapt")
    id("dagger.hilt.android.plugin")
    id("kotlin-parcelize")
    id("com.google.android.libraries.mapsplatform.secrets-gradle-plugin")
}

android {
    namespace = "com.runconnect"
    compileSdk = 34

    defaultConfig {
        applicationId = "com.runconnect"
        minSdk = 24
        targetSdk = 34
        versionCode = 1
        versionName = "1.0"

        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
        vectorDrawables {
            useSupportLibrary = true
        }
    }

    buildTypes {
        release {
            isMinifyEnabled = false
            proguardFiles(
                getDefaultProguardFile("proguard-android-optimize.txt"),
                "proguard-rules.pro"
            )
        }
    }

    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_1_8
        targetCompatibility = JavaVersion.VERSION_1_8
    }

    kotlinOptions {
        jvmTarget = "1.8"
    }

    buildFeatures {
        compose = true
        buildConfig = true
    }

    composeOptions {
        kotlinCompilerExtensionVersion = "1.5.4"
    }

    packaging {
        resources {
            excludes += "/META-INF/{AL2.0,LGPL2.1}"
        }
    }
}

dependencies {
    // Compose BOM
    implementation(platform("androidx.compose:compose-bom:2023.10.01"))
    implementation("androidx.compose.ui:ui")
    implementation("androidx.compose.ui:ui-graphics")
    implementation("androidx.compose.ui:ui-tooling-preview")
    implementation("androidx.compose.material3:material3")
    implementation("androidx.compose.material:material-icons-extended")

    // Core Android
    implementation("androidx.core:core-ktx:1.12.0")
    implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.7.0")
    implementation("androidx.activity:activity-compose:1.8.2")

    // Navigation
    implementation("androidx.navigation:navigation-compose:2.7.5")

    // ViewModel
    implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.7.0")

    // Hilt for DI
    implementation("com.google.dagger:hilt-android:2.48")
    implementation("androidx.hilt:hilt-navigation-compose:1.1.0")
    kapt("com.google.dagger:hilt-compiler:2.48")

    // Room Database
    implementation("androidx.room:room-runtime:2.6.0")
    implementation("androidx.room:room-ktx:2.6.0")
    kapt("androidx.room:room-compiler:2.6.0")

    // Network
    implementation("com.squareup.retrofit2:retrofit:2.9.0")
    implementation("com.squareup.retrofit2:converter-gson:2.9.0")
    implementation("com.squareup.okhttp3:logging-interceptor:4.12.0")

    // Location & Maps
    implementation("com.google.android.gms:play-services-location:21.0.1")
    implementation("com.google.android.gms:play-services-maps:18.2.0")
    implementation("com.google.maps.android:maps-compose:2.15.0")

    // Permissions
    implementation("com.google.accompanist:accompanist-permissions:0.32.0")

    // Image Loading
    implementation("io.coil-kt:coil-compose:2.5.0")

    // DataStore
    implementation("androidx.datastore:datastore-preferences:1.0.0")

    // Coroutines
    implementation("org.jetbrains.kotlinx:kotlinx-coroutines-play-services:1.7.3")

    // Google Auth
    implementation("com.google.android.gms:play-services-auth:20.7.0")

    // AdMob
    implementation("com.google.android.gms:play-services-ads:22.5.0")

    // Testing
    testImplementation("junit:junit:4.13.2")
    androidTestImplementation("androidx.test.ext:junit:1.1.5")
    androidTestImplementation("androidx.test.espresso:espresso-core:3.5.1")
    androidTestImplementation(platform("androidx.compose:compose-bom:2023.10.01"))
    androidTestImplementation("androidx.compose.ui:ui-test-junit4")
    debugImplementation("androidx.compose.ui:ui-tooling")
    debugImplementation("androidx.compose.ui:ui-test-manifest")
}
```

## 3. 도메인 모델 (Domain Models)

```kotlin
// domain/model/User.kt
data class User(
    val id: String,
    val email: String,
    val displayName: String,
    val profileImageUrl: String? = null,
    val totalDistance: Double = 0.0,
    val totalTime: Long = 0L,
    val averagePace: Double = 0.0,
    val level: Int = 1
)

// domain/model/RunningSession.kt
data class RunningSession(
    val id: String = "",
    val userId: String,
    val startTime: Long,
    val endTime: Long? = null,
    val distance: Double = 0.0,
    val duration: Long = 0L,
    val averagePace: Double = 0.0,
    val maxPace: Double = 0.0,
    val calories: Int = 0,
    val route: List<LocationPoint> = emptyList(),
    val isMatched: Boolean = false,
    val matchedUserId: String? = null,
    val status: RunningStatus = RunningStatus.PREPARING
)

// domain/model/LocationPoint.kt
data class LocationPoint(
    val latitude: Double,
    val longitude: Double,
    val timestamp: Long,
    val accuracy: Float = 0f
)

// domain/model/RunningStatus.kt
enum class RunningStatus {
    PREPARING,
    ACTIVE,
    PAUSED,
    COMPLETED,
    CANCELLED
}

// domain/model/MatchingRequest.kt
data class MatchingRequest(
    val userId: String,
    val currentLocation: LocationPoint,
    val preferredDistance: Double,
    val skillLevel: RunningLevel,
    val timestamp: Long
)

enum class RunningLevel {
    BEGINNER,    // < 7 min/km
    INTERMEDIATE, // 5-7 min/km
    ADVANCED,    // 4-5 min/km
    EXPERT       // < 4 min/km
}
```

## 4. 데이터 레이어

```kotlin
// data/local/RunningDatabase.kt
@Database(
    entities = [RunningSessionEntity::class, UserEntity::class],
    version = 1,
    exportSchema = false
)
@TypeConverters(Converters::class)
abstract class RunningDatabase : RoomDatabase() {
    abstract fun runningSessionDao(): RunningSessionDao
    abstract fun userDao(): UserDao
}

// data/local/entity/RunningSessionEntity.kt
@Entity(tableName = "running_sessions")
data class RunningSessionEntity(
    @PrimaryKey val id: String,
    val userId: String,
    val startTime: Long,
    val endTime: Long?,
    val distance: Double,
    val duration: Long,
    val averagePace: Double,
    val maxPace: Double,
    val calories: Int,
    val route: String, // JSON string of LocationPoint list
    val isMatched: Boolean,
    val matchedUserId: String?,
    val status: String
)

// data/local/dao/RunningSessionDao.kt
@Dao
interface RunningSessionDao {
    @Query("SELECT * FROM running_sessions WHERE userId = :userId ORDER BY startTime DESC")
    fun getAllSessionsForUser(userId: String): Flow<List<RunningSessionEntity>>
    
    @Query("SELECT * FROM running_sessions WHERE id = :sessionId")
    suspend fun getSessionById(sessionId: String): RunningSessionEntity?
    
    @Insert(onConflict = OnConflictStrategy.REPLACE)
    suspend fun insertSession(session: RunningSessionEntity)
    
    @Update
    suspend fun updateSession(session: RunningSessionEntity)
    
    @Query("SELECT * FROM running_sessions WHERE userId = :userId AND status = 'ACTIVE' LIMIT 1")
    suspend fun getActiveSession(userId: String): RunningSessionEntity?
}

// data/remote/api/RunningApiService.kt
interface RunningApiService {
    @POST("auth/login")
    suspend fun login(@Body loginRequest: LoginRequest): Response<AuthResponse>
    
    @GET("user/profile")
    suspend fun getUserProfile(@Header("Authorization") token: String): Response<UserResponse>
    
    @POST("running/session")
    suspend fun createRunningSession(
        @Header("Authorization") token: String,
        @Body session: CreateRunningSessionRequest
    ): Response<RunningSessionResponse>
    
    @PUT("running/session/{sessionId}")
    suspend fun updateRunningSession(
        @Header("Authorization") token: String,
        @Path("sessionId") sessionId: String,
        @Body session: UpdateRunningSessionRequest
    ): Response<RunningSessionResponse>
    
    @POST("matching/request")
    suspend fun requestMatching(
        @Header("Authorization") token: String,
        @Body request: MatchingRequest
    ): Response<MatchingResponse>
    
    @DELETE("matching/request")
    suspend fun cancelMatching(
        @Header("Authorization") token: String
    ): Response<Unit>
}

// data/repository/RunningRepositoryImpl.kt
@Singleton
class RunningRepositoryImpl @Inject constructor(
    private val apiService: RunningApiService,
    private val runningSessionDao: RunningSessionDao,
    private val userPreferences: UserPreferences
) : RunningRepository {
    
    override fun getRunningHistory(userId: String): Flow<List<RunningSession>> {
        return runningSessionDao.getAllSessionsForUser(userId)
            .map { entities -> entities.map { it.toDomainModel() } }
    }
    
    override suspend fun createRunningSession(session: RunningSession): Result<RunningSession> {
        return try {
            val token = userPreferences.getAuthToken()
            val response = apiService.createRunningSession(
                "Bearer $token",
                session.toCreateRequest()
            )
            
            if (response.isSuccessful) {
                val createdSession = response.body()?.toDomainModel()
                createdSession?.let {
                    runningSessionDao.insertSession(it.toEntity())
                }
                Result.success(createdSession!!)
            } else {
                Result.failure(Exception("Failed to create session"))
            }
        } catch (e: Exception) {
            Result.failure(e)
        }
    }
    
    override suspend fun updateRunningSession(session: RunningSession): Result<RunningSession> {
        return try {
            runningSessionDao.updateSession(session.toEntity())
            
            val token = userPreferences.getAuthToken()
            apiService.updateRunningSession(
                "Bearer $token",
                session.id,
                session.toUpdateRequest()
            )
            
            Result.success(session)
        } catch (e: Exception) {
            Result.failure(e)
        }
    }
    
    override suspend fun getActiveSession(userId: String): RunningSession? {
        return runningSessionDao.getActiveSession(userId)?.toDomainModel()
    }
    
    override suspend fun requestMatching(request: MatchingRequest): Result<String> {
        return try {
            val token = userPreferences.getAuthToken()
            val response = apiService.requestMatching("Bearer $token", request)
            
            if (response.isSuccessful) {
                Result.success(response.body()?.matchId ?: "")
            } else {
                Result.failure(Exception("Failed to request matching"))
            }
        } catch (e: Exception) {
            Result.failure(e)
        }
    }
}
```

## 5. 위치 서비스 (Location Service)

```kotlin
// utils/LocationService.kt
@AndroidEntryPoint
class LocationService : Service() {
    
    @Inject
    lateinit var runningRepository: RunningRepository
    
    @Inject
    lateinit var userPreferences: UserPreferences
    
    private val binder = LocationBinder()
    private lateinit var fusedLocationClient: FusedLocationProviderClient
    private lateinit var locationCallback: LocationCallback
    private var currentSession: RunningSession? = null
    private val locationPoints = mutableListOf<LocationPoint>()
    
    companion object {
        const val ACTION_START_TRACKING = "START_TRACKING"
        const val ACTION_STOP_TRACKING = "STOP_TRACKING"
        const val ACTION_PAUSE_TRACKING = "PAUSE_TRACKING"
        const val NOTIFICATION_ID = 1001
        const val CHANNEL_ID = "running_tracking"
    }
    
    inner class LocationBinder : Binder() {
        fun getService(): LocationService = this@LocationService
    }
    
    override fun onCreate() {
        super.onCreate()
        fusedLocationClient = LocationServices.getFusedLocationProviderClient(this)
        createNotificationChannel()
        setupLocationCallback()
    }
    
    override fun onBind(intent: Intent): IBinder = binder
    
    override fun onStartCommand(intent: Intent?, flags: Int, startId: Int): Int {
        when (intent?.action) {
            ACTION_START_TRACKING -> startLocationTracking()
            ACTION_PAUSE_TRACKING -> pauseLocationTracking()
            ACTION_STOP_TRACKING -> stopLocationTracking()
        }
        return START_STICKY
    }
    
    private fun setupLocationCallback() {
        locationCallback = object : LocationCallback() {
            override fun onLocationResult(locationResult: LocationResult) {
                super.onLocationResult(locationResult)
                
                locationResult.locations.forEach { location ->
                    val locationPoint = LocationPoint(
                        latitude = location.latitude,
                        longitude = location.longitude,
                        timestamp = System.currentTimeMillis(),
                        accuracy = location.accuracy
                    )
                    
                    locationPoints.add(locationPoint)
                    updateRunningSession(locationPoint)
                }
            }
        }
    }
    
    @SuppressLint("MissingPermission")
    private fun startLocationTracking() {
        val locationRequest = LocationRequest.Builder(Priority.PRIORITY_HIGH_ACCURACY, 1000)
            .setMinUpdateDistanceMeters(3f)
            .build()
        
        try {
            fusedLocationClient.requestLocationUpdates(
                locationRequest,
                locationCallback,
                Looper.getMainLooper()
            )
            
            startForeground(NOTIFICATION_ID, createNotification())
            
            // 새로운 런닝 세션 시작
            lifecycleScope.launch {
                val userId = userPreferences.getCurrentUserId()
                currentSession = RunningSession(
                    id = UUID.randomUUID().toString(),
                    userId = userId,
                    startTime = System.currentTimeMillis(),
                    status = RunningStatus.ACTIVE
                )
                runningRepository.createRunningSession(currentSession!!)
            }
        } catch (e: SecurityException) {
            Log.e("LocationService", "Location permission denied", e)
        }
    }
    
    private fun pauseLocationTracking() {
        currentSession?.let { session ->
            lifecycleScope.launch {
                val updatedSession = session.copy(status = RunningStatus.PAUSED)
                runningRepository.updateRunningSession(updatedSession)
                currentSession = updatedSession
            }
        }
        fusedLocationClient.removeLocationUpdates(locationCallback)
    }
    
    private fun stopLocationTracking() {
        fusedLocationClient.removeLocationUpdates(locationCallback)
        
        currentSession?.let { session ->
            lifecycleScope.launch {
                val endTime = System.currentTimeMillis()
                val totalDistance = calculateTotalDistance(locationPoints)
                val duration = endTime - session.startTime
                val averagePace = if (totalDistance > 0) duration / 1000.0 / (totalDistance / 1000.0) / 60.0 else 0.0
                
                val completedSession = session.copy(
                    endTime = endTime,
                    distance = totalDistance,
                    duration = duration,
                    averagePace = averagePace,
                    route = locationPoints.toList(),
                    status = RunningStatus.COMPLETED
                )
                
                runningRepository.updateRunningSession(completedSession)
            }
        }
        
        stopForeground(REMOVE_NOTIFICATION)
        stopSelf()
    }
    
    private fun updateRunningSession(newLocation: LocationPoint) {
        currentSession?.let { session ->
            lifecycleScope.launch {
                val totalDistance = calculateTotalDistance(locationPoints)
                val currentTime = System.currentTimeMillis()
                val duration = currentTime - session.startTime
                val averagePace = if (totalDistance > 0) duration / 1000.0 / (totalDistance / 1000.0) / 60.0 else 0.0
                
                val updatedSession = session.copy(
                    distance = totalDistance,
                    duration = duration,
                    averagePace = averagePace,
                    route = locationPoints.toList()
                )
                
                runningRepository.updateRunningSession(updatedSession)
                currentSession = updatedSession
                
                // 알림 업데이트
                val notification = createNotification(totalDistance, formatDuration(duration))
                val notificationManager = getSystemService(Context.NOTIFICATION_SERVICE) as NotificationManager
                notificationManager.notify(NOTIFICATION_ID, notification)
            }
        }
    }
    
    private fun calculateTotalDistance(points: List<LocationPoint>): Double {
        var totalDistance = 0.0
        for (i in 1 until points.size) {
            val results = FloatArray(1)
            Location.distanceBetween(
                points[i-1].latitude, points[i-1].longitude,
                points[i].latitude, points[i].longitude,
                results
            )
            totalDistance += results[0]
        }
        return totalDistance
    }
    
    private fun createNotification(distance: Double = 0.0, duration: String = "00:00"): Notification {
        val notificationIntent = Intent(this, MainActivity::class.java)
        val pendingIntent = PendingIntent.getActivity(
            this, 0, notificationIntent,
            PendingIntent.FLAG_UPDATE_CURRENT or PendingIntent.FLAG_IMMUTABLE
        )
        
        return NotificationCompat.Builder(this, CHANNEL_ID)
            .setContentTitle("런닝 중...")
            .setContentText("거리: ${String.format("%.2f", distance/1000)}km | 시간: $duration")
            .setSmallIcon(R.drawable.ic_running)
            .setContentIntent(pendingIntent)
            .setOngoing(true)
            .setCategory(NotificationCompat.CATEGORY_WORKOUT)
            .build()
    }
    
    private fun createNotificationChannel() {
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            val channel = NotificationChannel(
                CHANNEL_ID,
                "런닝 추적",
                NotificationManager.IMPORTANCE_LOW
            ).apply {
                description = "런닝 중 위치 추적 알림"
                setShowBadge(false)
            }
            
            val notificationManager = getSystemService(Context.NOTIFICATION_SERVICE) as NotificationManager
            notificationManager.createNotificationChannel(channel)
        }
    }
    
    private fun formatDuration(milliseconds: Long): String {
        val seconds = milliseconds / 1000
        val minutes = seconds / 60
        val hours = minutes / 60
        return if (hours > 0) {
            String.format("%02d:%02d:%02d", hours, minutes % 60, seconds % 60)
        } else {
            String.format("%02d:%02d", minutes, seconds % 60)
        }
    }
}
```

## 6. 주요 UI 화면 (Jetpack Compose)

```kotlin
// presentation/ui/home/HomeScreen.kt
@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun HomeScreen(
    onNavigateToSoloRun: () -> Unit,
    onNavigateToMatchedRun: () -> Unit,
    onNavigateToHistory: () -> Unit,
    onNavigateToProfile: () -> Unit,
    viewModel: HomeViewModel = hiltViewModel()
) {
    val uiState by viewModel.uiState.collectAsState()
    
    Scaffold(
        topBar = {
            TopAppBar(
                title = {
                    Text(
                        text = "RunConnect",
                        style = MaterialTheme.typography.headlineMedium.copy(
                            fontWeight = FontWeight.Bold,
                            color = MaterialTheme.colorScheme.primary
                        )
                    )
                },
                actions = {
                    IconButton(onClick = onNavigateToProfile) {
                        Icon(
                            imageVector = Icons.Default.Person,
                            contentDescription = "프로필"
                        )
                    }
                }
            )
        }
    ) { paddingValues ->
        LazyColumn(
            modifier = Modifier
                .fillMaxSize()
                .padding(paddingValues)
                .padding(horizontal = 16.dp),
            verticalArrangement = Arrangement.spacedBy(16.dp)
        ) {
            item {
                // 주간 요약 카드
                WeeklySummaryCard(
                    weeklyStats = uiState.weeklyStats,
                    modifier = Modifier.fillMaxWidth()
                )
            }
            
            item {
                // 런닝 모드 선택 버튼들
                Row(
                    modifier = Modifier.fillMaxWidth(),
                    horizontalArrangement = Arrangement.spacedBy(12.dp)
                ) {
                    RunningModeCard(
                        title = "솔로 런닝",
                        description = "혼자서 뛰기",
                        icon = Icons.Default.DirectionsRun,
                        onClick = onNavigateToSoloRun,
                        modifier = Modifier.weight(1f)
                    )
                    
                    RunningModeCard(
                        title = "매칭 런닝",
                        description = "다른 러너와 함께",
                        icon = Icons.Default.Group,
                        onClick = onNavigateToMatchedRun,
                        modifier = Modifier.weight(1f)
                    )
                }
            }
            
            item {
                // 최근 런닝 기록
                RecentRunsSection(
                    recentRuns = uiState.recentRuns,
                    onViewAllClick = onNavigateToHistory
                )
            }
            
            item {
                // 광고 배너
                AdBannerCard(
                    modifier = Modifier
                        .fillMaxWidth()
                        .height(60.dp)
                )
            }
        }
    }
}

@Composable
private fun WeeklySummaryCard(
    weeklyStats: WeeklyStats,
    modifier: Modifier = Modifier
) {
    Card(
        modifier = modifier,
        colors = CardDefaults.cardColors(
            containerColor = MaterialTheme.colorScheme.surface
        ),
        elevation = CardDefaults.cardElevation(defaultElevation = 2.dp)
    ) {
        Column(
            modifier = Modifier.padding(20.dp)
        ) {
            Text(
                text = "이번 주 런닝",
                style = MaterialTheme.typography.titleLarge.copy(
                    fontWeight = FontWeight.SemiBold
                ),
                color = MaterialTheme.colorScheme.onSurface
            )
            
            Spacer(modifier = Modifier.height(16.dp))
            
            Row(
                modifier = Modifier.fillMaxWidth(),
                horizontalArrangement = Arrangement.SpaceBetween
            ) {
                StatItem(
                    label = "거리",
                    value = "${String.format("%.1f", weeklyStats.totalDistance / 1000)}km",
                    icon = Icons.Default.Route
                )
                
                StatItem(
                    label = "시간",
                    value = formatDuration(weeklyStats.totalTime),
                    icon = Icons.Default.Timer
                )
                
                StatItem(
                    label = "칼로리",
                    value = "${weeklyStats.totalCalories}",
                    icon = Icons.Default.LocalFireDepartment
                )
            }
        }
    }
}

@Composable
private fun StatItem(
    label: String,
    value: String,
    icon: ImageVector,
    modifier: Modifier = Modifier
) {
    Column(
        modifier = modifier,
        horizontalAlignment = Alignment.CenterHorizontally
    ) {
        Icon(
            imageVector = icon,
            contentDescription = null,
            tint = MaterialTheme.colorScheme.primary,
            modifier = Modifier.size(24.dp)
        )
        
        Spacer(modifier = Modifier.height(8.dp))
        
        Text(
            text = value,
            style = MaterialTheme.typography.titleMedium.copy(
                fontWeight = FontWeight.Bold
            ),
            color = MaterialTheme.colorScheme.onSurface
        )
        
        Text(
            text = label,
            style = MaterialTheme.typography.bodySmall,
            color = MaterialTheme.colorScheme.onSurfaceVariant
        )
    }
}

@OptIn(ExperimentalMaterial3Api::class)
@Composable
private fun RunningModeCard(
    title: String,
    description: String,
    icon: ImageVector,
    onClick: () -> Unit,
    modifier: Modifier = Modifier
) {
    Card(
        onClick = onClick,
        modifier = modifier.height(120.dp),
        colors = CardDefaults.cardColors(
            containerColor = MaterialTheme.colorScheme.primaryContainer
        ),
        elevation = CardDefaults.cardElevation(defaultElevation = 4.dp)
    ) {
        Column(
            modifier = Modifier
                .fillMaxSize()
                .padding(16.dp),
            horizontalAlignment = Alignment.CenterHorizontally,
            verticalArrangement = Arrangement.Center
        ) {
            Icon(
                imageVector = icon,
                contentDescription = null,
                modifier = Modifier.size(32.dp),
                tint = MaterialTheme.colorScheme.onPrimaryContainer
            )
            
            Spacer(modifier = Modifier.height(8.dp))
            
            Text(
                text = title,
                style = MaterialTheme.typography.titleSmall.copy(
                    fontWeight = FontWeight.SemiBold
                ),
                color = MaterialTheme.colorScheme.onPrimaryContainer,
                textAlign = TextAlign.Center
            )
            
            Text(
                text = description,
                style = MaterialTheme.typography.bodySmall,
                color = MaterialTheme.colorScheme.onPrimaryContainer.copy(alpha = 0.7f),
                textAlign = TextAlign.Center
            )
        }
    }
}

// presentation/ui/running/RunningTrackingScreen.kt
@OptIn(ExperimentalPermissionsApi::class)
@Composable
fun RunningTrackingScreen(
    onNavigateBack: () -> Unit,
    onRunningComplete: (RunningSession) -> Unit,
    viewModel: RunningTrackingViewModel = hiltViewModel()
) {
    val uiState by viewModel.uiState.collectAsState()
    val context = LocalContext.current
    
    // 위치 권한 요청
    val locationPermissionState = rememberMultiplePermissionsState(
        listOf(
            Manifest.permission.ACCESS_FINE_LOCATION,
            Manifest.permission.ACCESS_COARSE_LOCATION
        )
    )
    
    LaunchedEffect(key1 = locationPermissionState.allPermissionsGranted) {
        if (locationPermissionState.allPermissionsGranted) {
            viewModel.startLocationTracking(context)
        }
    }
    
    if (!locationPermissionState.allPermissionsGranted) {
        LocationPermissionRequest(
            onRequestPermissions = { locationPermissionState.launchMultiplePermissionRequest() }
        )
    } else {
        RunningTrackingContent(
            uiState = uiState,
            onPauseClick = viewModel::pauseRunning,
            onResumeClick = viewModel::resumeRunning,
            onStopClick = {
                viewModel.stopRunning()
                onRunningComplete(uiState.currentSession!!)
            },
            onNavigateBack = onNavigateBack
        )
    }
}

@Composable
private fun RunningTrackingContent(
    uiState: RunningTrackingUiState,
    onPauseClick: () -> Unit,
    onResumeClick: () -> Unit,
    onStopClick: () -> Unit,
    onNavigateBack: () -> Unit
) {
    Box