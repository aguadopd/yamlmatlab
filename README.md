## yamlmatlab

This is a github copy of https://code.google.com/p/yamlmatlab/
that has been packaged into +yaml namespace by Yauhen Yakimovich.


## Installation

Just add the base folder to the Matlab path with:

```matlab
addpath('path/to/folder');
```

for example:
```matlab
addpath('D:\stuff\yamlmatlab-master\')
```


## Usage

### Reading in

```matlab
yaml_file = 'test.yaml';
YamlStruct = yaml.ReadYaml(yaml_file);
```

### Writing out

 ```matlab
 x.name='Martin';
 yaml.WriteYaml('test.yaml',x)
```

#### More options

Full sintax for writing is

```matlab
yaml.WriteYaml(filename, struct, flowstyle)
```

`flowstyle` is optional and its default value is 0.

- `0` outputs a fully indented and easy to read YAML file.
- `1` outputs a flow style, compact YAML file.

#### Example

```matlab
example_struct = struct('campo1','valor1','campo2',2,'campo3',struct('campo31',31','campo32',32),'campo4',4.0,'campo5',struct('campo51',struct('campo511',511)));

% Block style
yaml.WriteYaml('f0.yml', example_struct, 0); % Could be yaml.Write('f0.yml', example_struct);

% Flow style
yaml.WriteYaml('f1.yml', example_struct, 1);
```

```yaml
# f0.yml
campo1: valor1
campo2: 2.0
campo3:
  campo31: 31.0
  campo32: 32.0
campo4: 4.0
campo5:
  campo51:
    campo511: 511.0
```

```yaml
# f1.yml
{campo1: valor1, campo2: 2.0, campo3: {campo31: 31.0, campo32: 32.0}, campo4: 4.0,
  campo5: {campo51: {campo511: 511.0}}}
```



## Known issues

1. Special characters as well as whitespaces are not supported in field names

More automigrated issues can be found in [this repository](https://github.com/yangli625/yamlmatlab/issues).



## Others

- **https://learnxinyminutes.com/docs/yaml/**
- http://www.yaml.org/
- https://codebeautify.org/yaml-validator
- https://yaml-online-parser.appspot.com/


`yamlmatlab` depends on the [snakeyaml](https://bitbucket.org/asomov/snakeyaml/) YAML java processor.


## Main (and original) authors

* Jiri Cigler, Dept. of Control Engineering, CTU Prague http://support.dce.felk.cvut.cz/pub/ciglejir/
* Jan Siroky, Energocentrum PLUS, s.r.o.
* Pavel Tomasko, student at Faculty of Electrical Engineering, CTU Prague and Institute of Chemical Technology, Prague.
