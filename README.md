# envconfig

envconfig is a go module that loads a struct similar to the built-in json and
yaml tags used with structs.

## Usage

The struct should be in the following format:

```go
type Config struct {
	Foo           string        `env:"FOO" default:"5500"`
	Bar           time.Duration `env:"BAR" default:"24h"`
	Baz           int           `env:"BAZ" default:"0"`
	Fiz           bool          `env:"FIZ" default:"false"`
	Buz           float64       `env:"BUZ" default:"3.14"`
}
```

The struct can then be loaded as follows:

```go

func InitConfig(appname string) Config {
	var cfg Config
    	// Use the envconfig module to load from environment
	if err := envconfig.LoadFromEnv(&cfg); err != nil {
		// Handle error - you might want to log this or panic depending on your needs
		panic("Failed to load configuration: " + err.Error())
	}
    ...

```
