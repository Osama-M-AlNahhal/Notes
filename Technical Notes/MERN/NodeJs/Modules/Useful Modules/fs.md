
## Import module

```javascript
const fs = require('fs');
```

----

## Reading files

### readFile

```javascript
fs.readFile('./docs/blog.txt', (err, data) => {
	if (err) {
		console.log(err);
	}
	console.log(data.toString());
});
```

### readStream

```javascript
const readStream = fs.createReadStream('./docs/blog3.txt', { encoding: 'utf8'});

readStream.on('data', chunk => {
	console.log('---- NEW CHUNK ----');
	console.log(chunk);
});
```


----

## Writing files

### writeFile

```javascript
fs.writeFile('./docs/blog.txt', 'hello, world', () => {
	console.log('file was written');
});
```

### writeStream

```javascript
const writeStream = fs.createWriteStream('./docs/blog4.txt');
writeStream.write('something');
```


----

## piping

```javascript
readStream.pipe(writeStream);
```

----


## Directories (existsSync, mkdir & rmdir)

```javascript
if (!fs.existsSync('./assets')) {
	fs.mkdir('./assets', err => {
		if (err) {
			console.log(err);
		}
		console.log('folder created');
	});
} else {
	fs.rmdir('./assets', err => {
		if (err) {
			console.log(err);
		}
	console.log('folder deleted');
	});
}
```

----

## Deleting files (unlink)

```javascript
if (fs.existsSync('./docs/deleteme.txt')) {
	fs.unlink('./docs/deleteme.txt', err => {
		if (err) {
			console.log(err);
		}
		console.log('file deleted');
	});
}
```



----

