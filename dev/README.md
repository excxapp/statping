

# core
`import "github.com/hunterlong/statup/core"`

* [Overview](#pkg-overview)
* [Index](#pkg-index)
* [Subdirectories](#pkg-subdirectories)

## <a name="pkg-overview">Overview</a>
Package core contains the main functionality of Statup. This includes everything for
Services, Hits, Failures, Users, service checking mechanisms, databases, and notifiers
in the notifier package

More info on: <a href="https://github.com/hunterlong/statup">https://github.com/hunterlong/statup</a>




## <a name="pkg-index">Index</a>
* [Variables](#pkg-variables)
* [func CheckHash(password, hash string) bool](#CheckHash)
* [func CloseDB()](#CloseDB)
* [func CountFailures() uint64](#CountFailures)
* [func DatabaseMaintence()](#DatabaseMaintence)
* [func Dbtimestamp(group string, column string) string](#Dbtimestamp)
* [func DeleteAllSince(table string, date time.Time)](#DeleteAllSince)
* [func DeleteConfig()](#DeleteConfig)
* [func ExportChartsJs() string](#ExportChartsJs)
* [func ExportIndexHTML() string](#ExportIndexHTML)
* [func InitApp()](#InitApp)
* [func InsertLargeSampleData() error](#InsertLargeSampleData)
* [func InsertSampleData() error](#InsertSampleData)
* [func InsertSampleHits() error](#InsertSampleHits)
* [func SaveFile(filename string, data []byte) error](#SaveFile)
* [type Checkin](#Checkin)
  * [func ReturnCheckin(s *types.Checkin) *Checkin](#ReturnCheckin)
  * [func SelectCheckin(api string) *Checkin](#SelectCheckin)
  * [func (s *Checkin) AfterFind() (err error)](#Checkin.AfterFind)
  * [func (u *Checkin) BeforeCreate() (err error)](#Checkin.BeforeCreate)
  * [func (u *Checkin) Create() (int64, error)](#Checkin.Create)
  * [func (u *Checkin) Expected() time.Duration](#Checkin.Expected)
  * [func (u *Checkin) Grace() time.Duration](#Checkin.Grace)
  * [func (u *Checkin) Hits() []CheckinHit](#Checkin.Hits)
  * [func (u *Checkin) Last() CheckinHit](#Checkin.Last)
  * [func (u *Checkin) Period() time.Duration](#Checkin.Period)
  * [func (c *Checkin) RecheckCheckinFailure(guard chan struct{})](#Checkin.RecheckCheckinFailure)
  * [func (c *Checkin) String() string](#Checkin.String)
  * [func (u *Checkin) Update() (int64, error)](#Checkin.Update)
* [type CheckinHit](#CheckinHit)
  * [func ReturnCheckinHit(h *types.CheckinHit) *CheckinHit](#ReturnCheckinHit)
  * [func (s *CheckinHit) AfterFind() (err error)](#CheckinHit.AfterFind)
  * [func (f *CheckinHit) Ago() string](#CheckinHit.Ago)
  * [func (u *CheckinHit) BeforeCreate() (err error)](#CheckinHit.BeforeCreate)
  * [func (u *CheckinHit) Create() (int64, error)](#CheckinHit.Create)
* [type Core](#Core)
  * [func NewCore() *Core](#NewCore)
  * [func SelectCore() (*Core, error)](#SelectCore)
  * [func UpdateCore(c *Core) (*Core, error)](#UpdateCore)
  * [func (c Core) AllOnline() bool](#Core.AllOnline)
  * [func (c Core) BaseSASS() string](#Core.BaseSASS)
  * [func (c *Core) Count24HFailures() uint64](#Core.Count24HFailures)
  * [func (c *Core) CountOnline() int](#Core.CountOnline)
  * [func (c Core) CurrentTime() string](#Core.CurrentTime)
  * [func (c Core) MobileSASS() string](#Core.MobileSASS)
  * [func (c Core) SassVars() string](#Core.SassVars)
  * [func (c *Core) SelectAllServices() ([]*Service, error)](#Core.SelectAllServices)
  * [func (c *Core) ServicesCount() int](#Core.ServicesCount)
  * [func (c *Core) ToCore() *types.Core](#Core.ToCore)
  * [func (c Core) UsingAssets() bool](#Core.UsingAssets)
* [type DateScan](#DateScan)
* [type DateScanObj](#DateScanObj)
  * [func GraphDataRaw(service types.ServiceInterface, start, end time.Time, group string, column string) *DateScanObj](#GraphDataRaw)
  * [func (d *DateScanObj) ToString() string](#DateScanObj.ToString)
* [type DbConfig](#DbConfig)
  * [func LoadConfig(directory string) (*DbConfig, error)](#LoadConfig)
  * [func LoadUsingEnv() (*DbConfig, error)](#LoadUsingEnv)
  * [func (db *DbConfig) Close() error](#DbConfig.Close)
  * [func (db *DbConfig) Connect(retry bool, location string) error](#DbConfig.Connect)
  * [func (c *DbConfig) CreateCore() *Core](#DbConfig.CreateCore)
  * [func (db *DbConfig) CreateDatabase() error](#DbConfig.CreateDatabase)
  * [func (db *DbConfig) DropDatabase() error](#DbConfig.DropDatabase)
  * [func (db *DbConfig) InsertCore() (*Core, error)](#DbConfig.InsertCore)
  * [func (db *DbConfig) MigrateDatabase() error](#DbConfig.MigrateDatabase)
  * [func (c *DbConfig) Save() (*DbConfig, error)](#DbConfig.Save)
  * [func (c *DbConfig) Update() error](#DbConfig.Update)
* [type ErrorResponse](#ErrorResponse)
* [type Failure](#Failure)
  * [func (f *Failure) AfterFind() (err error)](#Failure.AfterFind)
  * [func (f *Failure) Ago() string](#Failure.Ago)
  * [func (u *Failure) BeforeCreate() (err error)](#Failure.BeforeCreate)
  * [func (f *Failure) Delete() error](#Failure.Delete)
  * [func (f *Failure) ParseError() string](#Failure.ParseError)
* [type Hit](#Hit)
  * [func (s *Hit) AfterFind() (err error)](#Hit.AfterFind)
  * [func (u *Hit) BeforeCreate() (err error)](#Hit.BeforeCreate)
* [type PluginJSON](#PluginJSON)
* [type PluginRepos](#PluginRepos)
* [type Service](#Service)
  * [func ReturnService(s *types.Service) *Service](#ReturnService)
  * [func SelectService(id int64) *Service](#SelectService)
  * [func (s *Service) AfterFind() (err error)](#Service.AfterFind)
  * [func (s *Service) AllFailures() []*Failure](#Service.AllFailures)
  * [func (s *Service) AvgTime() float64](#Service.AvgTime)
  * [func (s *Service) AvgUptime(ago time.Time) string](#Service.AvgUptime)
  * [func (s *Service) AvgUptime24() string](#Service.AvgUptime24)
  * [func (u *Service) BeforeCreate() (err error)](#Service.BeforeCreate)
  * [func (s *Service) Check(record bool)](#Service.Check)
  * [func (s *Service) CheckQueue(record bool)](#Service.CheckQueue)
  * [func (s *Service) Checkins() []*Checkin](#Service.Checkins)
  * [func (u *Service) Create(check bool) (int64, error)](#Service.Create)
  * [func (s *Service) CreateFailure(f *types.Failure) (int64, error)](#Service.CreateFailure)
  * [func (s *Service) CreateHit(h *types.Hit) (int64, error)](#Service.CreateHit)
  * [func (u *Service) Delete() error](#Service.Delete)
  * [func (u *Service) DeleteFailures()](#Service.DeleteFailures)
  * [func (s *Service) Downtime() time.Duration](#Service.Downtime)
  * [func (s *Service) DowntimeText() string](#Service.DowntimeText)
  * [func (s *Service) GraphData() string](#Service.GraphData)
  * [func (s *Service) Hits() ([]*types.Hit, error)](#Service.Hits)
  * [func (s *Service) HitsBetween(t1, t2 time.Time, group string, column string) *gorm.DB](#Service.HitsBetween)
  * [func (s *Service) LimitedFailures() []*Failure](#Service.LimitedFailures)
  * [func (s *Service) LimitedHits() ([]*types.Hit, error)](#Service.LimitedHits)
  * [func (s *Service) Online24() float32](#Service.Online24)
  * [func (s *Service) OnlineSince(ago time.Time) float32](#Service.OnlineSince)
  * [func (s *Service) Select() *types.Service](#Service.Select)
  * [func (s *Service) SmallText() string](#Service.SmallText)
  * [func (s *Service) Sum() (float64, error)](#Service.Sum)
  * [func (s *Service) ToJSON() string](#Service.ToJSON)
  * [func (s *Service) TotalFailures() (uint64, error)](#Service.TotalFailures)
  * [func (s *Service) TotalFailures24() (uint64, error)](#Service.TotalFailures24)
  * [func (s *Service) TotalFailuresSince(ago time.Time) (uint64, error)](#Service.TotalFailuresSince)
  * [func (s *Service) TotalHits() (uint64, error)](#Service.TotalHits)
  * [func (s *Service) TotalHitsSince(ago time.Time) (uint64, error)](#Service.TotalHitsSince)
  * [func (s *Service) TotalUptime() string](#Service.TotalUptime)
  * [func (u *Service) Update(restart bool) error](#Service.Update)
  * [func (u *Service) UpdateSingle(attr ...interface{}) error](#Service.UpdateSingle)
* [type ServiceOrder](#ServiceOrder)
  * [func (c ServiceOrder) Len() int](#ServiceOrder.Len)
  * [func (c ServiceOrder) Less(i, j int) bool](#ServiceOrder.Less)
  * [func (c ServiceOrder) Swap(i, j int)](#ServiceOrder.Swap)
* [type User](#User)
  * [func AuthUser(username, password string) (*User, bool)](#AuthUser)
  * [func ReturnUser(u *types.User) *User](#ReturnUser)
  * [func SelectAllUsers() ([]*User, error)](#SelectAllUsers)
  * [func SelectUser(id int64) (*User, error)](#SelectUser)
  * [func SelectUsername(username string) (*User, error)](#SelectUsername)
  * [func (u *User) AfterFind() (err error)](#User.AfterFind)
  * [func (u *User) BeforeCreate() (err error)](#User.BeforeCreate)
  * [func (u *User) Create() (int64, error)](#User.Create)
  * [func (u *User) Delete() error](#User.Delete)
  * [func (u *User) Update() error](#User.Update)


#### <a name="pkg-files">Package files</a>
[checker.go](https://github.com/hunterlong/statup/tree/master/core/checker.go) [checkin.go](https://github.com/hunterlong/statup/tree/master/core/checkin.go) [configs.go](https://github.com/hunterlong/statup/tree/master/core/configs.go) [core.go](https://github.com/hunterlong/statup/tree/master/core/core.go) [database.go](https://github.com/hunterlong/statup/tree/master/core/database.go) [doc.go](https://github.com/hunterlong/statup/tree/master/core/doc.go) [export.go](https://github.com/hunterlong/statup/tree/master/core/export.go) [failures.go](https://github.com/hunterlong/statup/tree/master/core/failures.go) [hits.go](https://github.com/hunterlong/statup/tree/master/core/hits.go) [sample.go](https://github.com/hunterlong/statup/tree/master/core/sample.go) [services.go](https://github.com/hunterlong/statup/tree/master/core/services.go) [users.go](https://github.com/hunterlong/statup/tree/master/core/users.go) 



## <a name="pkg-variables">Variables</a>
``` go
var (
    Configs   *DbConfig // Configs holds all of the config.yml and database info
    CoreApp   *Core     // CoreApp is a global variable that contains many elements
    SetupMode bool      // SetupMode will be true if Statup does not have a database connection
    VERSION   string    // VERSION is set on build automatically by setting a -ldflag
)
```
``` go
var (
    DbSession *gorm.DB
)
```


## <a name="CheckHash">func</a> [CheckHash](https://github.com/hunterlong/statup/tree/master/core/users.go?s=2896:2938#L105)
``` go
func CheckHash(password, hash string) bool
```
CheckHash returns true if the password matches with a hashed bcrypt password



## <a name="CloseDB">func</a> [CloseDB](https://github.com/hunterlong/statup/tree/master/core/database.go?s=2503:2517#L81)
``` go
func CloseDB()
```
CloseDB will close the database connection if available



## <a name="CountFailures">func</a> [CountFailures](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=2819:2846#L99)
``` go
func CountFailures() uint64
```
CountFailures returns the total count of failures for all services



## <a name="DatabaseMaintence">func</a> [DatabaseMaintence](https://github.com/hunterlong/statup/tree/master/core/database.go?s=7073:7097#L247)
``` go
func DatabaseMaintence()
```
DatabaseMaintence will automatically delete old records from 'failures' and 'hits'
this function is currently set to delete records 7+ days old every 60 minutes



## <a name="Dbtimestamp">func</a> [Dbtimestamp](https://github.com/hunterlong/statup/tree/master/core/services.go?s=5171:5223#L180)
``` go
func Dbtimestamp(group string, column string) string
```
Dbtimestamp will return a SQL query for grouping by date



## <a name="DeleteAllSince">func</a> [DeleteAllSince](https://github.com/hunterlong/statup/tree/master/core/database.go?s=7406:7455#L257)
``` go
func DeleteAllSince(table string, date time.Time)
```
DeleteAllSince will delete a specific table's records based on a time.



## <a name="DeleteConfig">func</a> [DeleteConfig](https://github.com/hunterlong/statup/tree/master/core/configs.go?s=3785:3804#L133)
``` go
func DeleteConfig()
```
DeleteConfig will delete the 'config.yml' file



## <a name="ExportChartsJs">func</a> [ExportChartsJs](https://github.com/hunterlong/statup/tree/master/core/export.go?s=2118:2146#L86)
``` go
func ExportChartsJs() string
```


## <a name="ExportIndexHTML">func</a> [ExportIndexHTML](https://github.com/hunterlong/statup/tree/master/core/export.go?s=889:918#L31)
``` go
func ExportIndexHTML() string
```


## <a name="InitApp">func</a> [InitApp](https://github.com/hunterlong/statup/tree/master/core/core.go?s=1690:1704#L60)
``` go
func InitApp()
```
InitApp will initialize Statup



## <a name="InsertLargeSampleData">func</a> [InsertLargeSampleData](https://github.com/hunterlong/statup/tree/master/core/sample.go?s=4671:4705#L179)
``` go
func InsertLargeSampleData() error
```
InsertSampleData will create the example/dummy services for a brand new Statup installation



## <a name="InsertSampleData">func</a> [InsertSampleData](https://github.com/hunterlong/statup/tree/master/core/sample.go?s=897:926#L27)
``` go
func InsertSampleData() error
```
InsertSampleData will create the example/dummy services for a brand new Statup installation



## <a name="InsertSampleHits">func</a> [InsertSampleHits](https://github.com/hunterlong/statup/tree/master/core/sample.go?s=3132:3161#L118)
``` go
func InsertSampleHits() error
```
InsertSampleHits will create a couple new hits for the sample services



## <a name="SaveFile">func</a> [SaveFile](https://github.com/hunterlong/statup/tree/master/core/export.go?s=2540:2589#L106)
``` go
func SaveFile(filename string, data []byte) error
```



## <a name="Checkin">type</a> [Checkin](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=818:857#L26)
``` go
type Checkin struct {
    *types.Checkin
}

```






### <a name="ReturnCheckin">func</a> [ReturnCheckin](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=1064:1109#L40)
``` go
func ReturnCheckin(s *types.Checkin) *Checkin
```
ReturnCheckin converts *types.Checking to *core.Checkin


### <a name="SelectCheckin">func</a> [SelectCheckin](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=1369:1408#L50)
``` go
func SelectCheckin(api string) *Checkin
```
SelectCheckin will find a Checkin based on the API supplied





### <a name="Checkin.AfterFind">func</a> (\*Checkin) [AfterFind](https://github.com/hunterlong/statup/tree/master/core/database.go?s=3376:3417#L117)
``` go
func (s *Checkin) AfterFind() (err error)
```
AfterFind for Checkin will set the timezone




### <a name="Checkin.BeforeCreate">func</a> (\*Checkin) [BeforeCreate](https://github.com/hunterlong/statup/tree/master/core/database.go?s=4403:4447#L161)
``` go
func (u *Checkin) BeforeCreate() (err error)
```
BeforeCreate for Checkin will set CreatedAt to UTC




### <a name="Checkin.Create">func</a> (\*Checkin) [Create](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=2642:2683#L92)
``` go
func (u *Checkin) Create() (int64, error)
```
Create will create a new Checkin




### <a name="Checkin.Expected">func</a> (\*Checkin) [Expected](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=2028:2070#L69)
``` go
func (u *Checkin) Expected() time.Duration
```
Expected returns the duration of when the serviec should receive a checkin




### <a name="Checkin.Grace">func</a> (\*Checkin) [Grace](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=1818:1857#L63)
``` go
func (u *Checkin) Grace() time.Duration
```
Grace will return the duration of the Checkin Grace Period (after service hasn't responded, wait a bit for a response)




### <a name="Checkin.Hits">func</a> (\*Checkin) [Hits](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=2442:2479#L85)
``` go
func (u *Checkin) Hits() []CheckinHit
```
Hits returns all of the CheckinHits for a given Checkin




### <a name="Checkin.Last">func</a> (\*Checkin) [Last](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=2255:2290#L78)
``` go
func (u *Checkin) Last() CheckinHit
```
Last returns the last CheckinHit for a Checkin




### <a name="Checkin.Period">func</a> (\*Checkin) [Period](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=1566:1606#L57)
``` go
func (u *Checkin) Period() time.Duration
```
Period will return the duration of the Checkin interval




### <a name="Checkin.RecheckCheckinFailure">func</a> (\*Checkin) [RecheckCheckinFailure](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=3622:3682#L132)
``` go
func (c *Checkin) RecheckCheckinFailure(guard chan struct{})
```
RecheckCheckinFailure will check if a Service Checkin has been reported yet




### <a name="Checkin.String">func</a> (\*Checkin) [String](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=949:982#L35)
``` go
func (c *Checkin) String() string
```
String will return a Checkin API string




### <a name="Checkin.Update">func</a> (\*Checkin) [Update](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=2884:2925#L103)
``` go
func (u *Checkin) Update() (int64, error)
```
Update will update a Checkin




## <a name="CheckinHit">type</a> [CheckinHit](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=859:904#L30)
``` go
type CheckinHit struct {
    *types.CheckinHit
}

```






### <a name="ReturnCheckinHit">func</a> [ReturnCheckinHit](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=1211:1265#L45)
``` go
func ReturnCheckinHit(h *types.CheckinHit) *CheckinHit
```
ReturnCheckinHit converts *types.CheckinHit to *core.CheckinHit





### <a name="CheckinHit.AfterFind">func</a> (\*CheckinHit) [AfterFind](https://github.com/hunterlong/statup/tree/master/core/database.go?s=3543:3587#L123)
``` go
func (s *CheckinHit) AfterFind() (err error)
```
AfterFind for CheckinHit will set the timezone




### <a name="CheckinHit.Ago">func</a> (\*CheckinHit) [Ago](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=3432:3465#L126)
``` go
func (f *CheckinHit) Ago() string
```
Ago returns the duration of time between now and the last successful CheckinHit




### <a name="CheckinHit.BeforeCreate">func</a> (\*CheckinHit) [BeforeCreate](https://github.com/hunterlong/statup/tree/master/core/database.go?s=4581:4628#L169)
``` go
func (u *CheckinHit) BeforeCreate() (err error)
```
BeforeCreate for CheckinHit will set CreatedAt to UTC




### <a name="CheckinHit.Create">func</a> (\*CheckinHit) [Create](https://github.com/hunterlong/statup/tree/master/core/checkin.go?s=3110:3154#L113)
``` go
func (u *CheckinHit) Create() (int64, error)
```
Create will create a new successful CheckinHit




## <a name="Core">type</a> [Core](https://github.com/hunterlong/statup/tree/master/core/core.go?s=967:1000#L31)
``` go
type Core struct {
    *types.Core
}

```






### <a name="NewCore">func</a> [NewCore](https://github.com/hunterlong/statup/tree/master/core/core.go?s=1426:1446#L47)
``` go
func NewCore() *Core
```
NewCore return a new *core.Core struct


### <a name="SelectCore">func</a> [SelectCore](https://github.com/hunterlong/statup/tree/master/core/core.go?s=3778:3810#L136)
``` go
func SelectCore() (*Core, error)
```
SelectCore will return the CoreApp global variable and the settings/configs for Statup


### <a name="UpdateCore">func</a> [UpdateCore](https://github.com/hunterlong/statup/tree/master/core/core.go?s=2257:2296#L82)
``` go
func UpdateCore(c *Core) (*Core, error)
```
UpdateCore will update the CoreApp variable inside of the 'core' table in database





### <a name="Core.AllOnline">func</a> (Core) [AllOnline](https://github.com/hunterlong/statup/tree/master/core/core.go?s=3552:3582#L126)
``` go
func (c Core) AllOnline() bool
```
AllOnline will be true if all services are online




### <a name="Core.BaseSASS">func</a> (Core) [BaseSASS](https://github.com/hunterlong/statup/tree/master/core/core.go?s=3055:3086#L109)
``` go
func (c Core) BaseSASS() string
```
BaseSASS is the base design , this opens the file /assets/scss/base.scss to be edited in Theme




### <a name="Core.Count24HFailures">func</a> (\*Core) [Count24HFailures](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=2547:2587#L88)
``` go
func (c *Core) Count24HFailures() uint64
```
Count24HFailures returns the amount of failures for a service within the last 24 hours




### <a name="Core.CountOnline">func</a> (\*Core) [CountOnline](https://github.com/hunterlong/statup/tree/master/core/services.go?s=10815:10847#L382)
``` go
func (c *Core) CountOnline() int
```
CountOnline




### <a name="Core.CurrentTime">func</a> (Core) [CurrentTime](https://github.com/hunterlong/statup/tree/master/core/core.go?s=2410:2444#L88)
``` go
func (c Core) CurrentTime() string
```
UsingAssets will return true if /assets folder is present




### <a name="Core.MobileSASS">func</a> (Core) [MobileSASS](https://github.com/hunterlong/statup/tree/master/core/core.go?s=3340:3373#L118)
``` go
func (c Core) MobileSASS() string
```
MobileSASS is the -webkit responsive custom css designs. This opens the
file /assets/scss/mobile.scss to be edited in Theme




### <a name="Core.SassVars">func</a> (Core) [SassVars](https://github.com/hunterlong/statup/tree/master/core/core.go?s=2797:2828#L101)
``` go
func (c Core) SassVars() string
```
SassVars opens the file /assets/scss/variables.scss to be edited in Theme




### <a name="Core.SelectAllServices">func</a> (\*Core) [SelectAllServices](https://github.com/hunterlong/statup/tree/master/core/services.go?s=1729:1783#L62)
``` go
func (c *Core) SelectAllServices() ([]*Service, error)
```
SelectAllServices returns a slice of *core.Service to be store on []*core.Services, should only be called once on startup.




### <a name="Core.ServicesCount">func</a> (\*Core) [ServicesCount](https://github.com/hunterlong/statup/tree/master/core/services.go?s=10736:10770#L377)
``` go
func (c *Core) ServicesCount() int
```
ServicesCount returns the amount of services inside the []*core.Services slice




### <a name="Core.ToCore">func</a> (\*Core) [ToCore](https://github.com/hunterlong/statup/tree/master/core/core.go?s=1600:1635#L55)
``` go
func (c *Core) ToCore() *types.Core
```
ToCore will convert *core.Core to *types.Core




### <a name="Core.UsingAssets">func</a> (Core) [UsingAssets](https://github.com/hunterlong/statup/tree/master/core/core.go?s=2638:2670#L96)
``` go
func (c Core) UsingAssets() bool
```
UsingAssets will return true if /assets folder is present




## <a name="DateScan">type</a> [DateScan](https://github.com/hunterlong/statup/tree/master/core/services.go?s=3675:3757#L133)
``` go
type DateScan struct {
    CreatedAt string `json:"x"`
    Value     int64  `json:"y"`
}

```
DateScan struct is for creating the charts.js graph JSON array










## <a name="DateScanObj">type</a> [DateScanObj](https://github.com/hunterlong/statup/tree/master/core/services.go?s=3828:3887#L139)
``` go
type DateScanObj struct {
    Array []DateScan `json:"data"`
}

```
DateScanObj struct is for creating the charts.js graph JSON array







### <a name="GraphDataRaw">func</a> [GraphDataRaw](https://github.com/hunterlong/statup/tree/master/core/services.go?s=6296:6409#L216)
``` go
func GraphDataRaw(service types.ServiceInterface, start, end time.Time, group string, column string) *DateScanObj
```
GraphDataRaw will return all the hits between 2 times for a Service





### <a name="DateScanObj.ToString">func</a> (\*DateScanObj) [ToString](https://github.com/hunterlong/statup/tree/master/core/services.go?s=7072:7111#L238)
``` go
func (d *DateScanObj) ToString() string
```
ToString will convert the DateScanObj into a JSON string for the charts to render




## <a name="DbConfig">type</a> [DbConfig](https://github.com/hunterlong/statup/tree/master/core/database.go?s=1099:1127#L37)
``` go
type DbConfig types.DbConfig
```






### <a name="LoadConfig">func</a> [LoadConfig](https://github.com/hunterlong/statup/tree/master/core/configs.go?s=1020:1072#L34)
``` go
func LoadConfig(directory string) (*DbConfig, error)
```
LoadConfig will attempt to load the 'config.yml' file in a specific directory


### <a name="LoadUsingEnv">func</a> [LoadUsingEnv](https://github.com/hunterlong/statup/tree/master/core/configs.go?s=1680:1718#L53)
``` go
func LoadUsingEnv() (*DbConfig, error)
```
LoadUsingEnv will attempt to load database configs based on environment variables. If DB_CONN is set if will force this function.





### <a name="DbConfig.Close">func</a> (\*DbConfig) [Close](https://github.com/hunterlong/statup/tree/master/core/database.go?s=2617:2650#L88)
``` go
func (db *DbConfig) Close() error
```
Close shutsdown the database connection




### <a name="DbConfig.Connect">func</a> (\*DbConfig) [Connect](https://github.com/hunterlong/statup/tree/master/core/database.go?s=5265:5327#L193)
``` go
func (db *DbConfig) Connect(retry bool, location string) error
```
Connect will attempt to connect to the sqlite, postgres, or mysql database




### <a name="DbConfig.CreateCore">func</a> (\*DbConfig) [CreateCore](https://github.com/hunterlong/statup/tree/master/core/database.go?s=8558:8595#L304)
``` go
func (c *DbConfig) CreateCore() *Core
```
CreateCore will initialize the global variable 'CoreApp". This global variable contains most of Statup app.




### <a name="DbConfig.CreateDatabase">func</a> (\*DbConfig) [CreateDatabase](https://github.com/hunterlong/statup/tree/master/core/database.go?s=9609:9651#L340)
``` go
func (db *DbConfig) CreateDatabase() error
```
CreateDatabase will CREATE TABLES for each of the Statup elements




### <a name="DbConfig.DropDatabase">func</a> (\*DbConfig) [DropDatabase](https://github.com/hunterlong/statup/tree/master/core/database.go?s=9055:9095#L326)
``` go
func (db *DbConfig) DropDatabase() error
```
DropDatabase will DROP each table Statup created




### <a name="DbConfig.InsertCore">func</a> (\*DbConfig) [InsertCore](https://github.com/hunterlong/statup/tree/master/core/database.go?s=4773:4820#L177)
``` go
func (db *DbConfig) InsertCore() (*Core, error)
```
InsertCore create the single row for the Core settings in Statup




### <a name="DbConfig.MigrateDatabase">func</a> (\*DbConfig) [MigrateDatabase](https://github.com/hunterlong/statup/tree/master/core/database.go?s=10390:10433#L357)
``` go
func (db *DbConfig) MigrateDatabase() error
```
MigrateDatabase will migrate the database structure to current version.
This function will NOT remove previous records, tables or columns from the database.
If this function has an issue, it will ROLLBACK to the previous state.




### <a name="DbConfig.Save">func</a> (\*DbConfig) [Save](https://github.com/hunterlong/statup/tree/master/core/database.go?s=8035:8079#L284)
``` go
func (c *DbConfig) Save() (*DbConfig, error)
```
Save will initially create the config.yml file




### <a name="DbConfig.Update">func</a> (\*DbConfig) [Update](https://github.com/hunterlong/statup/tree/master/core/database.go?s=7674:7707#L266)
``` go
func (c *DbConfig) Update() error
```
Update will save the config.yml file




## <a name="ErrorResponse">type</a> [ErrorResponse](https://github.com/hunterlong/statup/tree/master/core/configs.go?s=894:937#L29)
``` go
type ErrorResponse struct {
    Error string
}

```
ErrorResponse is used for HTTP errors to show to user










## <a name="Failure">type</a> [Failure](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=829:868#L27)
``` go
type Failure struct {
    *types.Failure
}

```









### <a name="Failure.AfterFind">func</a> (\*Failure) [AfterFind](https://github.com/hunterlong/statup/tree/master/core/database.go?s=3054:3095#L105)
``` go
func (f *Failure) AfterFind() (err error)
```
AfterFind for Failure will set the timezone




### <a name="Failure.Ago">func</a> (\*Failure) [Ago](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=2207:2237#L76)
``` go
func (f *Failure) Ago() string
```
Ago returns a human readable timestamp for a failure




### <a name="Failure.BeforeCreate">func</a> (\*Failure) [BeforeCreate](https://github.com/hunterlong/statup/tree/master/core/database.go?s=3884:3928#L137)
``` go
func (u *Failure) BeforeCreate() (err error)
```
BeforeCreate for Failure will set CreatedAt to UTC




### <a name="Failure.Delete">func</a> (\*Failure) [Delete](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=2372:2404#L82)
``` go
func (f *Failure) Delete() error
```
Delete will remove a failure record from the database




### <a name="Failure.ParseError">func</a> (\*Failure) [ParseError](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=3855:3892#L132)
``` go
func (f *Failure) ParseError() string
```
ParseError returns a human readable error for a failure




## <a name="Hit">type</a> [Hit](https://github.com/hunterlong/statup/tree/master/core/hits.go?s=782:813#L24)
``` go
type Hit struct {
    *types.Hit
}

```









### <a name="Hit.AfterFind">func</a> (\*Hit) [AfterFind](https://github.com/hunterlong/statup/tree/master/core/database.go?s=2894:2931#L99)
``` go
func (s *Hit) AfterFind() (err error)
```
AfterFind for Hit will set the timezone




### <a name="Hit.BeforeCreate">func</a> (\*Hit) [BeforeCreate](https://github.com/hunterlong/statup/tree/master/core/database.go?s=3713:3753#L129)
``` go
func (u *Hit) BeforeCreate() (err error)
```
BeforeCreate for Hit will set CreatedAt to UTC




## <a name="PluginJSON">type</a> [PluginJSON](https://github.com/hunterlong/statup/tree/master/core/core.go?s=898:930#L28)
``` go
type PluginJSON types.PluginJSON
```









## <a name="PluginRepos">type</a> [PluginRepos](https://github.com/hunterlong/statup/tree/master/core/core.go?s=931:965#L29)
``` go
type PluginRepos types.PluginRepos
```









## <a name="Service">type</a> [Service](https://github.com/hunterlong/statup/tree/master/core/services.go?s=900:939#L30)
``` go
type Service struct {
    *types.Service
}

```






### <a name="ReturnService">func</a> [ReturnService](https://github.com/hunterlong/statup/tree/master/core/services.go?s=1128:1173#L40)
``` go
func ReturnService(s *types.Service) *Service
```
ReturnService will convert *types.Service to *core.Service


### <a name="SelectService">func</a> [SelectService](https://github.com/hunterlong/statup/tree/master/core/services.go?s=1255:1292#L45)
``` go
func SelectService(id int64) *Service
```
SelectService returns a *core.Service from in memory





### <a name="Service.AfterFind">func</a> (\*Service) [AfterFind](https://github.com/hunterlong/statup/tree/master/core/database.go?s=2734:2775#L93)
``` go
func (s *Service) AfterFind() (err error)
```
AfterFind for Service will set the timezone




### <a name="Service.AllFailures">func</a> (\*Service) [AllFailures](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=1249:1291#L44)
``` go
func (s *Service) AllFailures() []*Failure
```
AllFailures will return all failures attached to a service




### <a name="Service.AvgTime">func</a> (\*Service) [AvgTime](https://github.com/hunterlong/statup/tree/master/core/services.go?s=2596:2631#L92)
``` go
func (s *Service) AvgTime() float64
```
AvgTime will return the average amount of time for a service to response back successfully




### <a name="Service.AvgUptime">func</a> (\*Service) [AvgUptime](https://github.com/hunterlong/statup/tree/master/core/services.go?s=7817:7866#L267)
``` go
func (s *Service) AvgUptime(ago time.Time) string
```
AvgUptime returns average online status for last 24 hours




### <a name="Service.AvgUptime24">func</a> (\*Service) [AvgUptime24](https://github.com/hunterlong/statup/tree/master/core/services.go?s=7647:7685#L261)
``` go
func (s *Service) AvgUptime24() string
```
AvgUptime24 returns a service's average online status for last 24 hours




### <a name="Service.BeforeCreate">func</a> (\*Service) [BeforeCreate](https://github.com/hunterlong/statup/tree/master/core/database.go?s=4228:4272#L153)
``` go
func (u *Service) BeforeCreate() (err error)
```
BeforeCreate for Service will set CreatedAt to UTC




### <a name="Service.Check">func</a> (\*Service) [Check](https://github.com/hunterlong/statup/tree/master/core/checker.go?s=5538:5574#L222)
``` go
func (s *Service) Check(record bool)
```
Check will run checkHttp for HTTP services and checkTcp for TCP services




### <a name="Service.CheckQueue">func</a> (\*Service) [CheckQueue](https://github.com/hunterlong/statup/tree/master/core/checker.go?s=1256:1297#L43)
``` go
func (s *Service) CheckQueue(record bool)
```
CheckQueue is the main go routine for checking a service




### <a name="Service.Checkins">func</a> (\*Service) [Checkins](https://github.com/hunterlong/statup/tree/master/core/services.go?s=1463:1502#L55)
``` go
func (s *Service) Checkins() []*Checkin
```
Checkins will return a slice of Checkins for a Service




### <a name="Service.Create">func</a> (\*Service) [Create](https://github.com/hunterlong/statup/tree/master/core/services.go?s=10250:10301#L361)
``` go
func (u *Service) Create(check bool) (int64, error)
```
Create will create a service and insert it into the database




### <a name="Service.CreateFailure">func</a> (\*Service) [CreateFailure](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=934:998#L32)
``` go
func (s *Service) CreateFailure(f *types.Failure) (int64, error)
```
CreateFailure will create a new failure record for a service




### <a name="Service.CreateHit">func</a> (\*Service) [CreateHit](https://github.com/hunterlong/statup/tree/master/core/hits.go?s=907:963#L29)
``` go
func (s *Service) CreateHit(h *types.Hit) (int64, error)
```
CreateHit will create a new 'hit' record in the database for a successful/online service




### <a name="Service.Delete">func</a> (\*Service) [Delete](https://github.com/hunterlong/statup/tree/master/core/services.go?s=9104:9136#L321)
``` go
func (u *Service) Delete() error
```
Delete will remove a service from the database, it will also end the service checking go routine




### <a name="Service.DeleteFailures">func</a> (\*Service) [DeleteFailures](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=1672:1706#L59)
``` go
func (u *Service) DeleteFailures()
```
DeleteFailures will delete all failures for a service




### <a name="Service.Downtime">func</a> (\*Service) [Downtime](https://github.com/hunterlong/statup/tree/master/core/services.go?s=5906:5948#L202)
``` go
func (s *Service) Downtime() time.Duration
```
Downtime returns the amount of time of a offline service




### <a name="Service.DowntimeText">func</a> (\*Service) [DowntimeText](https://github.com/hunterlong/statup/tree/master/core/services.go?s=4970:5009#L175)
``` go
func (s *Service) DowntimeText() string
```
DowntimeText will return the amount of downtime for a service based on the duration




### <a name="Service.GraphData">func</a> (\*Service) [GraphData](https://github.com/hunterlong/statup/tree/master/core/services.go?s=7303:7339#L248)
``` go
func (s *Service) GraphData() string
```
GraphData returns the JSON object used by Charts.js to render the chart




### <a name="Service.Hits">func</a> (\*Service) [Hits](https://github.com/hunterlong/statup/tree/master/core/hits.go?s=1139:1185#L39)
``` go
func (s *Service) Hits() ([]*types.Hit, error)
```
Hits returns all successful hits for a service




### <a name="Service.HitsBetween">func</a> (\*Service) [HitsBetween](https://github.com/hunterlong/statup/tree/master/core/database.go?s=2097:2182#L75)
``` go
func (s *Service) HitsBetween(t1, t2 time.Time, group string, column string) *gorm.DB
```
HitsBetween returns the gorm database query for a collection of service hits between a time range




### <a name="Service.LimitedFailures">func</a> (\*Service) [LimitedFailures](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=1964:2010#L68)
``` go
func (s *Service) LimitedFailures() []*Failure
```
LimitedFailures will return the last 10 failures from a service




### <a name="Service.LimitedHits">func</a> (\*Service) [LimitedHits](https://github.com/hunterlong/statup/tree/master/core/hits.go?s=1406:1459#L47)
``` go
func (s *Service) LimitedHits() ([]*types.Hit, error)
```
LimitedHits returns the last 1024 successful/online 'hit' records for a service




### <a name="Service.Online24">func</a> (\*Service) [Online24](https://github.com/hunterlong/statup/tree/master/core/services.go?s=2922:2958#L105)
``` go
func (s *Service) Online24() float32
```
Online24 returns the service's uptime percent within last 24 hours




### <a name="Service.OnlineSince">func</a> (\*Service) [OnlineSince](https://github.com/hunterlong/statup/tree/master/core/services.go?s=3122:3174#L111)
``` go
func (s *Service) OnlineSince(ago time.Time) float32
```
OnlineSince accepts a time since parameter to return the percent of a service's uptime.




### <a name="Service.Select">func</a> (\*Service) [Select](https://github.com/hunterlong/statup/tree/master/core/services.go?s=1001:1042#L35)
``` go
func (s *Service) Select() *types.Service
```
Select will return the *types.Service struct for Service




### <a name="Service.SmallText">func</a> (\*Service) [SmallText](https://github.com/hunterlong/statup/tree/master/core/services.go?s=4172:4208#L154)
``` go
func (s *Service) SmallText() string
```
SmallText returns a short description about a services status




### <a name="Service.Sum">func</a> (\*Service) [Sum](https://github.com/hunterlong/statup/tree/master/core/hits.go?s=2458:2498#L79)
``` go
func (s *Service) Sum() (float64, error)
```
Sum returns the added value Latency for all of the services successful hits.




### <a name="Service.ToJSON">func</a> (\*Service) [ToJSON](https://github.com/hunterlong/statup/tree/master/core/services.go?s=2414:2447#L86)
``` go
func (s *Service) ToJSON() string
```
ToJSON will convert a service to a JSON string




### <a name="Service.TotalFailures">func</a> (\*Service) [TotalFailures](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=3270:3319#L116)
``` go
func (s *Service) TotalFailures() (uint64, error)
```
TotalFailures returns the total amount of failures for a service




### <a name="Service.TotalFailures24">func</a> (\*Service) [TotalFailures24](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=3071:3122#L110)
``` go
func (s *Service) TotalFailures24() (uint64, error)
```
TotalFailures24 returns the amount of failures for a service within the last 24 hours




### <a name="Service.TotalFailuresSince">func</a> (\*Service) [TotalFailuresSince](https://github.com/hunterlong/statup/tree/master/core/failures.go?s=3544:3611#L124)
``` go
func (s *Service) TotalFailuresSince(ago time.Time) (uint64, error)
```
TotalFailuresSince returns the total amount of failures for a service since a specific time/date




### <a name="Service.TotalHits">func</a> (\*Service) [TotalHits](https://github.com/hunterlong/statup/tree/master/core/hits.go?s=1889:1934#L63)
``` go
func (s *Service) TotalHits() (uint64, error)
```
TotalHits returns the total amount of successful hits a service has




### <a name="Service.TotalHitsSince">func</a> (\*Service) [TotalHitsSince](https://github.com/hunterlong/statup/tree/master/core/hits.go?s=2134:2197#L71)
``` go
func (s *Service) TotalHitsSince(ago time.Time) (uint64, error)
```
TotalHitsSince returns the total amount of hits based on a specific time/date




### <a name="Service.TotalUptime">func</a> (\*Service) [TotalUptime](https://github.com/hunterlong/statup/tree/master/core/services.go?s=8292:8330#L289)
``` go
func (s *Service) TotalUptime() string
```
TotalUptime returns the total uptime percent of a service




### <a name="Service.Update">func</a> (\*Service) [Update](https://github.com/hunterlong/statup/tree/master/core/services.go?s=9766:9810#L342)
``` go
func (u *Service) Update(restart bool) error
```
Update will update a service in the database, the service's checking routine can be restarted by passing true




### <a name="Service.UpdateSingle">func</a> (\*Service) [UpdateSingle](https://github.com/hunterlong/statup/tree/master/core/services.go?s=9541:9598#L337)
``` go
func (u *Service) UpdateSingle(attr ...interface{}) error
```
UpdateSingle will update a single column for a service




## <a name="ServiceOrder">type</a> [ServiceOrder](https://github.com/hunterlong/statup/tree/master/core/core.go?s=4393:4435#L158)
``` go
type ServiceOrder []types.ServiceInterface
```
ServiceOrder will reorder the services based on 'order_id' (Order)










### <a name="ServiceOrder.Len">func</a> (ServiceOrder) [Len](https://github.com/hunterlong/statup/tree/master/core/core.go?s=4437:4468#L160)
``` go
func (c ServiceOrder) Len() int
```



### <a name="ServiceOrder.Less">func</a> (ServiceOrder) [Less](https://github.com/hunterlong/statup/tree/master/core/core.go?s=4567:4608#L162)
``` go
func (c ServiceOrder) Less(i, j int) bool
```



### <a name="ServiceOrder.Swap">func</a> (ServiceOrder) [Swap](https://github.com/hunterlong/statup/tree/master/core/core.go?s=4497:4533#L161)
``` go
func (c ServiceOrder) Swap(i, j int)
```



## <a name="User">type</a> [User](https://github.com/hunterlong/statup/tree/master/core/users.go?s=819:852#L26)
``` go
type User struct {
    *types.User
}

```






### <a name="AuthUser">func</a> [AuthUser](https://github.com/hunterlong/statup/tree/master/core/users.go?s=2574:2628#L92)
``` go
func AuthUser(username, password string) (*User, bool)
```
AuthUser will return the User and a boolean if authentication was correct.
AuthUser accepts username, and password as a string


### <a name="ReturnUser">func</a> [ReturnUser](https://github.com/hunterlong/statup/tree/master/core/users.go?s=911:947#L31)
``` go
func ReturnUser(u *types.User) *User
```
ReturnUser returns *core.User based off a *types.User


### <a name="SelectAllUsers">func</a> [SelectAllUsers](https://github.com/hunterlong/statup/tree/master/core/users.go?s=2229:2267#L81)
``` go
func SelectAllUsers() ([]*User, error)
```
SelectAllUsers returns all users


### <a name="SelectUser">func</a> [SelectUser](https://github.com/hunterlong/statup/tree/master/core/users.go?s=1025:1065#L36)
``` go
func SelectUser(id int64) (*User, error)
```
SelectUser returns the User based on the user's ID.


### <a name="SelectUsername">func</a> [SelectUsername](https://github.com/hunterlong/statup/tree/master/core/users.go?s=1206:1257#L43)
``` go
func SelectUsername(username string) (*User, error)
```
SelectUser returns the User based on the user's username





### <a name="User.AfterFind">func</a> (\*User) [AfterFind](https://github.com/hunterlong/statup/tree/master/core/database.go?s=3215:3253#L111)
``` go
func (u *User) AfterFind() (err error)
```
AfterFind for USer will set the timezone




### <a name="User.BeforeCreate">func</a> (\*User) [BeforeCreate](https://github.com/hunterlong/statup/tree/master/core/database.go?s=4056:4097#L145)
``` go
func (u *User) BeforeCreate() (err error)
```
BeforeCreate for User will set CreatedAt to UTC




### <a name="User.Create">func</a> (\*User) [Create](https://github.com/hunterlong/statup/tree/master/core/users.go?s=1790:1828#L64)
``` go
func (u *User) Create() (int64, error)
```
Create will insert a new user into the database




### <a name="User.Delete">func</a> (\*User) [Delete](https://github.com/hunterlong/statup/tree/master/core/users.go?s=1434:1463#L51)
``` go
func (u *User) Delete() error
```
Delete will remove the user record from the database




### <a name="User.Update">func</a> (\*User) [Update](https://github.com/hunterlong/statup/tree/master/core/users.go?s=1555:1584#L56)
``` go
func (u *User) Update() error
```
Update will update the user's record in database










> cmd
Package main for building the Statup CLI binary application. This package
connects to all the other packages to make a runnable binary for multiple
operating system.

To build Statup from source, run the follow command in the root directory:
// go build -o statup ./cmd

Remember that you'll need to compile the static assets using Rice:
// cd source && rice embed-go

More info on: <a href="https://github.com/hunterlong/statup">https://github.com/hunterlong/statup</a>








# handlers
`import "github.com/hunterlong/statup/handlers"`

* [Overview](#pkg-overview)
* [Index](#pkg-index)

## <a name="pkg-overview">Overview</a>
Package handlers contains the HTTP server along with the requests and routes. All HTTP related
functions are in this package.

More info on: <a href="https://github.com/hunterlong/statup">https://github.com/hunterlong/statup</a>




## <a name="pkg-index">Index</a>
* [func DesktopInit(ip string, port int)](#DesktopInit)
* [func IsAuthenticated(r *http.Request) bool](#IsAuthenticated)
* [func Router() *mux.Router](#Router)
* [func RunHTTPServer(ip string, port int) error](#RunHTTPServer)
* [type PluginSelect](#PluginSelect)


#### <a name="pkg-files">Package files</a>
[api.go](https://github.com/hunterlong/statup/tree/master/handlers/api.go) [dashboard.go](https://github.com/hunterlong/statup/tree/master/handlers/dashboard.go) [doc.go](https://github.com/hunterlong/statup/tree/master/handlers/doc.go) [handlers.go](https://github.com/hunterlong/statup/tree/master/handlers/handlers.go) [index.go](https://github.com/hunterlong/statup/tree/master/handlers/index.go) [plugins.go](https://github.com/hunterlong/statup/tree/master/handlers/plugins.go) [prometheus.go](https://github.com/hunterlong/statup/tree/master/handlers/prometheus.go) [routes.go](https://github.com/hunterlong/statup/tree/master/handlers/routes.go) [services.go](https://github.com/hunterlong/statup/tree/master/handlers/services.go) [settings.go](https://github.com/hunterlong/statup/tree/master/handlers/settings.go) [setup.go](https://github.com/hunterlong/statup/tree/master/handlers/setup.go) [users.go](https://github.com/hunterlong/statup/tree/master/handlers/users.go) 





## <a name="DesktopInit">func</a> [DesktopInit](https://github.com/hunterlong/statup/tree/master/handlers/index.go?s=1194:1231#L41)
``` go
func DesktopInit(ip string, port int)
```


## <a name="IsAuthenticated">func</a> [IsAuthenticated](https://github.com/hunterlong/statup/tree/master/handlers/handlers.go?s=2049:2091#L68)
``` go
func IsAuthenticated(r *http.Request) bool
```
IsAuthenticated returns true if the HTTP request is authenticated. You can set the environment variable GO_ENV=test
to bypass the admin authenticate to the dashboard features.



## <a name="Router">func</a> [Router](https://github.com/hunterlong/statup/tree/master/handlers/routes.go?s=980:1005#L34)
``` go
func Router() *mux.Router
```
Router returns all of the routes used in Statup



## <a name="RunHTTPServer">func</a> [RunHTTPServer](https://github.com/hunterlong/statup/tree/master/handlers/handlers.go?s=1141:1186#L43)
``` go
func RunHTTPServer(ip string, port int) error
```
RunHTTPServer will start a HTTP server on a specific IP and port




## <a name="PluginSelect">type</a> [PluginSelect](https://github.com/hunterlong/statup/tree/master/handlers/plugins.go?s=725:814#L23)
``` go
type PluginSelect struct {
    Plugin string
    Form   string
    Params map[string]interface{}
}

```















# notifiers
`import "github.com/hunterlong/statup/notifiers"`

* [Overview](#pkg-overview)
* [Index](#pkg-index)

## <a name="pkg-overview">Overview</a>
Package notifiers holds all the notifiers for Statup, which also includes
user created notifiers that have been accepted in a Push Request. Read the wiki
to see a full example of a notifier with all events, visit Statup's
notifier example code: <a href="https://github.com/hunterlong/statup/wiki/Notifier-Example">https://github.com/hunterlong/statup/wiki/Notifier-Example</a>

This package shouldn't contain any exports, to see how notifiers work
visit the core/notifier package at: <a href="https://godoc.org/github.com/hunterlong/statup/core/notifier">https://godoc.org/github.com/hunterlong/statup/core/notifier</a>
and learn how to create your own custom notifier.




## <a name="pkg-index">Index</a>


#### <a name="pkg-files">Package files</a>
[discord.go](https://github.com/hunterlong/statup/tree/master/notifiers/discord.go) [doc.go](https://github.com/hunterlong/statup/tree/master/notifiers/doc.go) [email.go](https://github.com/hunterlong/statup/tree/master/notifiers/email.go) [line_notify.go](https://github.com/hunterlong/statup/tree/master/notifiers/line_notify.go) [slack.go](https://github.com/hunterlong/statup/tree/master/notifiers/slack.go) [twilio.go](https://github.com/hunterlong/statup/tree/master/notifiers/twilio.go) [webhook.go](https://github.com/hunterlong/statup/tree/master/notifiers/webhook.go) 












# source
`import "github.com/hunterlong/statup/source"`

* [Overview](#pkg-overview)
* [Index](#pkg-index)

## <a name="pkg-overview">Overview</a>
Package source holds all the assets for Statup. This includes
CSS, JS, SCSS, HTML and other website related content.
This package uses Rice to compile all assets into a single 'rice-box.go' file.

To compile all the assets run `rice embed-go` in the source directory.

More info on: <a href="https://github.com/hunterlong/statup">https://github.com/hunterlong/statup</a>




## <a name="pkg-index">Index</a>
* [Variables](#pkg-variables)
* [func Assets()](#Assets)
* [func CompileSASS(folder string) error](#CompileSASS)
* [func CopyToPublic(box *rice.Box, folder, file string) error](#CopyToPublic)
* [func CreateAllAssets(folder string) error](#CreateAllAssets)
* [func DeleteAllAssets(folder string) error](#DeleteAllAssets)
* [func HelpMarkdown() string](#HelpMarkdown)
* [func MakePublicFolder(folder string) error](#MakePublicFolder)
* [func OpenAsset(folder, file string) string](#OpenAsset)
* [func SaveAsset(data []byte, folder, file string) error](#SaveAsset)
* [func UsingAssets(folder string) bool](#UsingAssets)


#### <a name="pkg-files">Package files</a>
[doc.go](https://github.com/hunterlong/statup/tree/master/source/doc.go) [rice-box.go](https://github.com/hunterlong/statup/tree/master/source/rice-box.go) [source.go](https://github.com/hunterlong/statup/tree/master/source/source.go) 



## <a name="pkg-variables">Variables</a>
``` go
var (
    CssBox  *rice.Box // CSS files from the 'source/css' directory, this will be loaded into '/assets/css'
    ScssBox *rice.Box // SCSS files from the 'source/scss' directory, this will be loaded into '/assets/scss'
    JsBox   *rice.Box // JS files from the 'source/js' directory, this will be loaded into '/assets/js'
    TmplBox *rice.Box // HTML and other small files from the 'source/tmpl' directory, this will be loaded into '/assets'
)
```


## <a name="Assets">func</a> [Assets](https://github.com/hunterlong/statup/tree/master/source/source.go?s=1380:1393#L38)
``` go
func Assets()
```
Assets will load the Rice boxes containing the CSS, SCSS, JS, and HTML files.



## <a name="CompileSASS">func</a> [CompileSASS](https://github.com/hunterlong/statup/tree/master/source/source.go?s=1872:1909#L57)
``` go
func CompileSASS(folder string) error
```
CompileSASS will attempt to compile the SASS files into CSS



## <a name="CopyToPublic">func</a> [CopyToPublic](https://github.com/hunterlong/statup/tree/master/source/source.go?s=6311:6370#L190)
``` go
func CopyToPublic(box *rice.Box, folder, file string) error
```
CopyToPublic will create a file from a rice Box to the '/assets' directory



## <a name="CreateAllAssets">func</a> [CreateAllAssets](https://github.com/hunterlong/statup/tree/master/source/source.go?s=4588:4629#L152)
``` go
func CreateAllAssets(folder string) error
```
CreateAllAssets will dump HTML, CSS, SCSS, and JS assets into the '/assets' directory



## <a name="DeleteAllAssets">func</a> [DeleteAllAssets](https://github.com/hunterlong/statup/tree/master/source/source.go?s=5969:6010#L179)
``` go
func DeleteAllAssets(folder string) error
```
DeleteAllAssets will delete the '/assets' folder



## <a name="HelpMarkdown">func</a> [HelpMarkdown](https://github.com/hunterlong/statup/tree/master/source/source.go?s=1599:1625#L46)
``` go
func HelpMarkdown() string
```
HelpMarkdown will return the Markdown of help.md into HTML



## <a name="MakePublicFolder">func</a> [MakePublicFolder](https://github.com/hunterlong/statup/tree/master/source/source.go?s=6878:6920#L207)
``` go
func MakePublicFolder(folder string) error
```
MakePublicFolder will create a new folder



## <a name="OpenAsset">func</a> [OpenAsset](https://github.com/hunterlong/statup/tree/master/source/source.go?s=4278:4320#L142)
``` go
func OpenAsset(folder, file string) string
```
OpenAsset returns a file's contents as a string



## <a name="SaveAsset">func</a> [SaveAsset](https://github.com/hunterlong/statup/tree/master/source/source.go?s=3910:3964#L131)
``` go
func SaveAsset(data []byte, folder, file string) error
```
SaveAsset will save an asset to the '/assets/' folder.



## <a name="UsingAssets">func</a> [UsingAssets](https://github.com/hunterlong/statup/tree/master/source/source.go?s=3365:3401#L111)
``` go
func UsingAssets(folder string) bool
```
UsingAssets returns true if the '/assets' folder is found in the directory










# types
`import "github.com/hunterlong/statup/types"`

* [Overview](#pkg-overview)
* [Index](#pkg-index)

## <a name="pkg-overview">Overview</a>
Package types contains all of the structs for objects in Statup including services, hits, failures, Core, and others.

More info on: <a href="https://github.com/hunterlong/statup">https://github.com/hunterlong/statup</a>




## <a name="pkg-index">Index</a>
* [Constants](#pkg-constants)
* [Variables](#pkg-variables)
* [type AllNotifiers](#AllNotifiers)
* [type Checkin](#Checkin)
* [type CheckinHit](#CheckinHit)
* [type Core](#Core)
* [type CoreInterface](#CoreInterface)
* [type DbConfig](#DbConfig)
* [type Failure](#Failure)
* [type FailureInterface](#FailureInterface)
* [type Hit](#Hit)
* [type Info](#Info)
* [type PluginActions](#PluginActions)
* [type PluginInfo](#PluginInfo)
* [type PluginJSON](#PluginJSON)
* [type PluginRepos](#PluginRepos)
* [type Routing](#Routing)
* [type Service](#Service)
  * [func (s *Service) Close()](#Service.Close)
  * [func (s *Service) IsRunning() bool](#Service.IsRunning)
  * [func (s *Service) Start()](#Service.Start)
* [type ServiceInterface](#ServiceInterface)
* [type User](#User)
* [type UserInterface](#UserInterface)


#### <a name="pkg-files">Package files</a>
[checkin.go](https://github.com/hunterlong/statup/tree/master/types/checkin.go) [core.go](https://github.com/hunterlong/statup/tree/master/types/core.go) [doc.go](https://github.com/hunterlong/statup/tree/master/types/doc.go) [failure.go](https://github.com/hunterlong/statup/tree/master/types/failure.go) [service.go](https://github.com/hunterlong/statup/tree/master/types/service.go) [time.go](https://github.com/hunterlong/statup/tree/master/types/time.go) [types.go](https://github.com/hunterlong/statup/tree/master/types/types.go) [user.go](https://github.com/hunterlong/statup/tree/master/types/user.go) 


## <a name="pkg-constants">Constants</a>
``` go
const (
    TIME_NANOZ = "2006-01-02 15:04:05.999999-0700 MST"
    TIME_NANO  = "2006-01-02T15:04:05Z"
    TIME       = "2006-01-02 15:04:05"
    TIME_DAY   = "2006-01-02"
)
```

## <a name="pkg-variables">Variables</a>
``` go
var (
    NOW         = func() time.Time { return time.Now() }()
    HOUR_1_AGO  = time.Now().Add(-1 * time.Hour)
    HOUR_24_AGO = time.Now().Add(-24 * time.Hour)
    HOUR_72_AGO = time.Now().Add(-72 * time.Hour)
    DAY_7_AGO   = NOW.AddDate(0, 0, -7)
    MONTH_1_AGO = NOW.AddDate(0, -1, 0)
    YEAR_1_AGO  = NOW.AddDate(-1, 0, 0)
)
```



## <a name="AllNotifiers">type</a> [AllNotifiers](https://github.com/hunterlong/statup/tree/master/types/core.go?s=707:736#L22)
``` go
type AllNotifiers interface{}
```









## <a name="Checkin">type</a> [Checkin](https://github.com/hunterlong/statup/tree/master/types/checkin.go?s=707:1126#L22)
``` go
type Checkin struct {
    Id          int64     `gorm:"primary_key;column:id"`
    Service     int64     `gorm:"index;column:service"`
    Interval    int64     `gorm:"column:check_interval"`
    GracePeriod int64     `gorm:"column:grace_period"`
    ApiKey      string    `gorm:"column:api_key"`
    CreatedAt   time.Time `gorm:"column:created_at" json:"created_at"`
    UpdatedAt   time.Time `gorm:"column:updated_at" json:"updated_at"`
}

```









## <a name="CheckinHit">type</a> [CheckinHit](https://github.com/hunterlong/statup/tree/master/types/checkin.go?s=1128:1374#L32)
``` go
type CheckinHit struct {
    Id        int64     `gorm:"primary_key;column:id"`
    Checkin   int64     `gorm:"index;column:checkin"`
    From      string    `gorm:"column:from_location"`
    CreatedAt time.Time `gorm:"column:created_at" json:"created_at"`
}

```









## <a name="Core">type</a> [Core](https://github.com/hunterlong/statup/tree/master/types/core.go?s=990:2624#L27)
``` go
type Core struct {
    Name          string             `gorm:"not null;column:name" json:"name"`
    Description   string             `gorm:"not null;column:description" json:"description,omitempty"`
    Config        string             `gorm:"column:config" json:"-"`
    ApiKey        string             `gorm:"column:api_key" json:"-"`
    ApiSecret     string             `gorm:"column:api_secret" json:"-"`
    Style         string             `gorm:"not null;column:style" json:"style,omitempty"`
    Footer        string             `gorm:"not null;column:footer" json:"footer,omitempty"`
    Domain        string             `gorm:"not null;column:domain" json:"domain,omitempty"`
    Version       string             `gorm:"column:version" json:"version"`
    MigrationId   int64              `gorm:"column:migration_id" json:"migration_id,omitempty"`
    UseCdn        bool               `gorm:"column:use_cdn;default:false" json:"using_cdn,omitempty"`
    Timezone      float32            `gorm:"column:timezone;default:-8.0" json:"timezone,omitempty"`
    CreatedAt     time.Time          `gorm:"column:created_at" json:"created_at"`
    UpdatedAt     time.Time          `gorm:"column:updated_at" json:"updated_at"`
    DbConnection  string             `gorm:"-" json:"database"`
    Started       time.Time          `gorm:"-" json:"started_on"`
    Services      []ServiceInterface `gorm:"-" json:"services,omitempty"`
    Plugins       []Info             `gorm:"-" json:"-"`
    Repos         []PluginJSON       `gorm:"-" json:"-"`
    AllPlugins    []PluginActions    `gorm:"-" json:"-"`
    Notifications []AllNotifiers     `gorm:"-" json:"-"`
    CoreInterface `gorm:"-" json:"-"`
}

```
Core struct contains all the required fields for Statup. All application settings
will be saved into 1 row in the 'core' table. You can use the core.CoreApp
global variable to interact with the attributes to the application, such as services.










## <a name="CoreInterface">type</a> [CoreInterface](https://github.com/hunterlong/statup/tree/master/types/core.go?s=2626:2766#L52)
``` go
type CoreInterface interface {
    SelectAllServices() ([]*Service, error)
    Count24HFailures() uint64
    ServicesCount() int
    CountOnline() int
}
```









## <a name="DbConfig">type</a> [DbConfig](https://github.com/hunterlong/statup/tree/master/types/types.go?s=1166:1740#L34)
``` go
type DbConfig struct {
    DbConn      string `yaml:"connection"`
    DbHost      string `yaml:"host"`
    DbUser      string `yaml:"user"`
    DbPass      string `yaml:"password"`
    DbData      string `yaml:"database"`
    DbPort      int    `yaml:"port"`
    ApiKey      string `yaml:"api_key"`
    ApiSecret   string `yaml:"api_secret"`
    Project     string `yaml:"-"`
    Description string `yaml:"-"`
    Domain      string `yaml:"-"`
    Username    string `yaml:"-"`
    Password    string `yaml:"-"`
    Email       string `yaml:"-"`
    Error       error  `yaml:"-"`
    Location    string `yaml:"location"`
}

```
DbConfig struct is used for the database connection and creates the 'config.yml' file










## <a name="Failure">type</a> [Failure](https://github.com/hunterlong/statup/tree/master/types/failure.go?s=862:1324#L24)
``` go
type Failure struct {
    Id               int64     `gorm:"primary_key;column:id" json:"id"`
    Issue            string    `gorm:"column:issue" json:"issue"`
    Method           string    `gorm:"column:method" json:"method,omitempty"`
    Service          int64     `gorm:"index;column:service" json:"-"`
    PingTime         float64   `gorm:"column:ping_time"`
    CreatedAt        time.Time `gorm:"column:created_at" json:"created_at"`
    FailureInterface `gorm:"-" json:"-"`
}

```
Failure is a failed attempt to check a service. Any a service does not meet the expected requirements,
a new Failure will be inserted into database.










## <a name="FailureInterface">type</a> [FailureInterface](https://github.com/hunterlong/statup/tree/master/types/failure.go?s=1326:1511#L34)
``` go
type FailureInterface interface {
    Ago() string        // Ago returns a human readble timestamp
    ParseError() string // ParseError returns a human readable error for a service failure
}
```









## <a name="Hit">type</a> [Hit](https://github.com/hunterlong/statup/tree/master/types/types.go?s=819:1075#L25)
``` go
type Hit struct {
    Id        int64     `gorm:"primary_key;column:id"`
    Service   int64     `gorm:"column:service"`
    Latency   float64   `gorm:"column:latency"`
    PingTime  float64   `gorm:"column:ping_time"`
    CreatedAt time.Time `gorm:"column:created_at"`
}

```
Hit struct is a 'successful' ping or web response entry for a service.










## <a name="Info">type</a> [Info](https://github.com/hunterlong/statup/tree/master/types/types.go?s=1742:1822#L53)
``` go
type Info struct {
    Name        string
    Description string
    Form        string
}

```









## <a name="PluginActions">type</a> [PluginActions](https://github.com/hunterlong/statup/tree/master/types/types.go?s=1985:2596#L70)
``` go
type PluginActions interface {
    GetInfo() Info
    GetForm() string
    OnLoad(db gorm.DB)
    SetInfo(map[string]interface{}) Info
    Routes() []Routing
    OnSave(map[string]interface{})
    OnFailure(map[string]interface{})
    OnSuccess(map[string]interface{})
    OnSettingsSaved(map[string]interface{})
    OnNewUser(map[string]interface{})
    OnNewService(map[string]interface{})
    OnUpdatedService(map[string]interface{})
    OnDeletedService(map[string]interface{})
    OnInstall(map[string]interface{})
    OnUninstall(map[string]interface{})
    OnBeforeRequest(map[string]interface{})
    OnAfterRequest(map[string]interface{})
    OnShutdown()
}
```









## <a name="PluginInfo">type</a> [PluginInfo](https://github.com/hunterlong/statup/tree/master/types/types.go?s=1824:1876#L59)
``` go
type PluginInfo struct {
    Info Info
    PluginActions
}

```









## <a name="PluginJSON">type</a> [PluginJSON](https://github.com/hunterlong/statup/tree/master/types/types.go?s=2649:2859#L95)
``` go
type PluginJSON struct {
    Name        string `json:"name"`
    Description string `json:"description"`
    Repo        string `json:"repo"`
    Author      string `json:"author"`
    Namespace   string `json:"namespace"`
}

```









## <a name="PluginRepos">type</a> [PluginRepos](https://github.com/hunterlong/statup/tree/master/types/types.go?s=2598:2647#L91)
``` go
type PluginRepos struct {
    Plugins []PluginJSON
}

```









## <a name="Routing">type</a> [Routing](https://github.com/hunterlong/statup/tree/master/types/types.go?s=1878:1983#L64)
``` go
type Routing struct {
    URL     string
    Method  string
    Handler func(http.ResponseWriter, *http.Request)
}

```









## <a name="Service">type</a> [Service](https://github.com/hunterlong/statup/tree/master/types/service.go?s=707:2484#L22)
``` go
type Service struct {
    Id             int64         `gorm:"primary_key;column:id" json:"id"`
    Name           string        `gorm:"column:name" json:"name"`
    Domain         string        `gorm:"column:domain" json:"domain"`
    Expected       string        `gorm:"not null;column:expected" json:"expected"`
    ExpectedStatus int           `gorm:"default:200;column:expected_status" json:"expected_status"`
    Interval       int           `gorm:"default:30;column:check_interval" json:"check_interval"`
    Type           string        `gorm:"column:check_type" json:"type"`
    Method         string        `gorm:"column:method" json:"method"`
    PostData       string        `gorm:"not null;column:post_data" json:"post_data"`
    Port           int           `gorm:"not null;column:port" json:"port"`
    Timeout        int           `gorm:"default:30;column:timeout" json:"timeout"`
    Order          int           `gorm:"default:0;column:order_id" json:"order_id"`
    CreatedAt      time.Time     `gorm:"column:created_at" json:"created_at"`
    UpdatedAt      time.Time     `gorm:"column:updated_at" json:"updated_at"`
    Online         bool          `gorm:"-" json:"online"`
    Latency        float64       `gorm:"-" json:"latency"`
    PingTime       float64       `gorm:"-" json:"ping_time"`
    Online24Hours  float32       `gorm:"-" json:"24_hours_online"`
    AvgResponse    string        `gorm:"-" json:"avg_response"`
    Running        chan bool     `gorm:"-" json:"-"`
    Checkpoint     time.Time     `gorm:"-" json:"-"`
    SleepDuration  time.Duration `gorm:"-" json:"-"`
    LastResponse   string        `gorm:"-" json:"-"`
    LastStatusCode int           `gorm:"-" json:"status_code"`
    LastOnline     time.Time     `gorm:"-" json:"last_online"`
    Failures       []interface{} `gorm:"-" json:"failures,omitempty"`
}

```









### <a name="Service.Close">func</a> (\*Service) [Close](https://github.com/hunterlong/statup/tree/master/types/service.go?s=2844:2869#L66)
``` go
func (s *Service) Close()
```
Close will stop the go routine that is checking if service is online or not




### <a name="Service.IsRunning">func</a> (\*Service) [IsRunning](https://github.com/hunterlong/statup/tree/master/types/service.go?s=2980:3014#L73)
``` go
func (s *Service) IsRunning() bool
```
IsRunning returns true if the service go routine is running




### <a name="Service.Start">func</a> (\*Service) [Start](https://github.com/hunterlong/statup/tree/master/types/service.go?s=2705:2730#L61)
``` go
func (s *Service) Start()
```
Start will create a channel for the service checking go routine




## <a name="ServiceInterface">type</a> [ServiceInterface](https://github.com/hunterlong/statup/tree/master/types/service.go?s=2486:2636#L51)
``` go
type ServiceInterface interface {
    Select() *Service
    CheckQueue(bool)
    Check(bool)
    Create(bool) (int64, error)
    Update(bool) error
    Delete() error
}
```









## <a name="User">type</a> [User](https://github.com/hunterlong/statup/tree/master/types/user.go?s=707:1393#L22)
``` go
type User struct {
    Id            int64     `gorm:"primary_key;column:id" json:"id"`
    Username      string    `gorm:"type:varchar(100);unique;column:username;" json:"username"`
    Password      string    `gorm:"column:password" json:"-"`
    Email         string    `gorm:"type:varchar(100);unique;column:email" json:"-"`
    ApiKey        string    `gorm:"column:api_key" json:"api_key"`
    ApiSecret     string    `gorm:"column:api_secret" json:"-"`
    Admin         bool      `gorm:"column:administrator" json:"admin"`
    CreatedAt     time.Time `gorm:"column:created_at" json:"created_at"`
    UpdatedAt     time.Time `gorm:"column:updated_at" json:"updated_at"`
    UserInterface `gorm:"-" json:"-"`
}

```









## <a name="UserInterface">type</a> [UserInterface](https://github.com/hunterlong/statup/tree/master/types/user.go?s=1395:1507#L35)
``` go
type UserInterface interface {
    // Database functions
    Create() (int64, error)
    Update() error
    Delete() error
}
```















# utils
`import "github.com/hunterlong/statup/utils"`

* [Overview](#pkg-overview)
* [Index](#pkg-index)

## <a name="pkg-overview">Overview</a>
Package utils contains common methods used in most packages in Statup.
This package contains multiple function like:
Logging, encryption, type conversions, setting utils.Directory as the current directory,
running local CMD commands, and creaing/deleting files/folder.

You can overwrite the utils.Directory global variable by including
STATUP_DIR environment variable to be an absolute path.

More info on: <a href="https://github.com/hunterlong/statup">https://github.com/hunterlong/statup</a>




## <a name="pkg-index">Index</a>
* [Variables](#pkg-variables)
* [func Command(cmd string) (string, string, error)](#Command)
* [func DeleteDirectory(directory string) error](#DeleteDirectory)
* [func DeleteFile(file string) error](#DeleteFile)
* [func DurationReadable(d time.Duration) string](#DurationReadable)
* [func FileExists(name string) bool](#FileExists)
* [func FormatDuration(d time.Duration) string](#FormatDuration)
* [func HashPassword(password string) string](#HashPassword)
* [func Http(r *http.Request) string](#Http)
* [func InitLogs() error](#InitLogs)
* [func Log(level int, err interface{}) error](#Log)
* [func NewSHA1Hash(n ...int) string](#NewSHA1Hash)
* [func RandomString(n int) string](#RandomString)
* [func StringInt(s string) int64](#StringInt)
* [func Timezoner(t time.Time, zone float32) time.Time](#Timezoner)
* [func ToString(s interface{}) string](#ToString)
* [func UnderScoreString(str string) string](#UnderScoreString)
* [type LogRow](#LogRow)
  * [func GetLastLine() *LogRow](#GetLastLine)
  * [func (o *LogRow) FormatForHtml() string](#LogRow.FormatForHtml)
* [type Timestamp](#Timestamp)
  * [func (t Timestamp) Ago() string](#Timestamp.Ago)
* [type Timestamper](#Timestamper)


#### <a name="pkg-files">Package files</a>
[doc.go](https://github.com/hunterlong/statup/tree/master/utils/doc.go) [encryption.go](https://github.com/hunterlong/statup/tree/master/utils/encryption.go) [log.go](https://github.com/hunterlong/statup/tree/master/utils/log.go) [time.go](https://github.com/hunterlong/statup/tree/master/utils/time.go) [utils.go](https://github.com/hunterlong/statup/tree/master/utils/utils.go) 



## <a name="pkg-variables">Variables</a>
``` go
var (
    LastLines []*LogRow
    LockLines sync.Mutex
)
```
``` go
var (
    Directory string
)
```


## <a name="Command">func</a> [Command](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=3477:3525#L146)
``` go
func Command(cmd string) (string, string, error)
```
Command will run a terminal command with 'sh -c COMMAND' and return stdout and errOut as strings



## <a name="DeleteDirectory">func</a> [DeleteDirectory](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=3295:3339#L141)
``` go
func DeleteDirectory(directory string) error
```
DeleteDirectory will attempt to delete a directory and all contents inside



## <a name="DeleteFile">func</a> [DeleteFile](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=3076:3110#L131)
``` go
func DeleteFile(file string) error
```
DeleteFile will attempt to delete a file



## <a name="DurationReadable">func</a> [DurationReadable](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=4663:4708#L200)
``` go
func DurationReadable(d time.Duration) string
```


## <a name="FileExists">func</a> [FileExists](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=2889:2922#L121)
``` go
func FileExists(name string) bool
```
FileExists returns true if a file exists



## <a name="FormatDuration">func</a> [FormatDuration](https://github.com/hunterlong/statup/tree/master/utils/time.go?s=714:757#L23)
``` go
func FormatDuration(d time.Duration) string
```


## <a name="HashPassword">func</a> [HashPassword](https://github.com/hunterlong/statup/tree/master/utils/encryption.go?s=825:866#L26)
``` go
func HashPassword(password string) string
```
HashPassword returns the bcrypt hash of a password string



## <a name="Http">func</a> [Http](https://github.com/hunterlong/statup/tree/master/utils/log.go?s=3070:3103#L126)
``` go
func Http(r *http.Request) string
```
Http returns a log for a HTTP request



## <a name="InitLogs">func</a> [InitLogs](https://github.com/hunterlong/statup/tree/master/utils/log.go?s=1415:1436#L58)
``` go
func InitLogs() error
```
InitLogs will create the '/logs' directory and creates a file '/logs/statup.log' for application logging



## <a name="Log">func</a> [Log](https://github.com/hunterlong/statup/tree/master/utils/log.go?s=2191:2233#L93)
``` go
func Log(level int, err interface{}) error
```
Log creates a new entry in the Logger. Log has 1-5 levels depending on how critical the log/error is



## <a name="NewSHA1Hash">func</a> [NewSHA1Hash](https://github.com/hunterlong/statup/tree/master/utils/encryption.go?s=1026:1059#L32)
``` go
func NewSHA1Hash(n ...int) string
```
NewSHA1Hash returns a random SHA1 hash based on a specific length



## <a name="RandomString">func</a> [RandomString](https://github.com/hunterlong/statup/tree/master/utils/encryption.go?s=1439:1470#L47)
``` go
func RandomString(n int) string
```
RandomString generates a random string of n length



## <a name="StringInt">func</a> [StringInt](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=1100:1130#L45)
``` go
func StringInt(s string) int64
```
StringInt converts a string to an int64



## <a name="Timezoner">func</a> [Timezoner](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=1530:1581#L69)
``` go
func Timezoner(t time.Time, zone float32) time.Time
```


## <a name="ToString">func</a> [ToString](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=1221:1256#L51)
``` go
func ToString(s interface{}) string
```
ToString converts a int to a string



## <a name="UnderScoreString">func</a> [UnderScoreString](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=2204:2244#L97)
``` go
func UnderScoreString(str string) string
```
UnderScoreString will return a string that replaces spaces and other characters to underscores




## <a name="LogRow">type</a> [LogRow](https://github.com/hunterlong/statup/tree/master/utils/log.go?s=3739:3795#L154)
``` go
type LogRow struct {
    Date time.Time
    Line interface{}
}

```






### <a name="GetLastLine">func</a> [GetLastLine](https://github.com/hunterlong/statup/tree/master/utils/log.go?s=3586:3612#L145)
``` go
func GetLastLine() *LogRow
```
GetLastLine returns 1 line for a recent log entry





### <a name="LogRow.FormatForHtml">func</a> (\*LogRow) [FormatForHtml](https://github.com/hunterlong/statup/tree/master/utils/log.go?s=4105:4144#L178)
``` go
func (o *LogRow) FormatForHtml() string
```



## <a name="Timestamp">type</a> [Timestamp](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=1838:1862#L85)
``` go
type Timestamp time.Time
```









### <a name="Timestamp.Ago">func</a> (Timestamp) [Ago](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=1996:2027#L91)
``` go
func (t Timestamp) Ago() string
```
Ago returns a human readable timestamp based on the Timestamp (time.Time) interface




## <a name="Timestamper">type</a> [Timestamper](https://github.com/hunterlong/statup/tree/master/utils/utils.go?s=1863:1907#L86)
``` go
type Timestamper interface {
    Ago() string
}
```












