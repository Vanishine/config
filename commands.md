## Docker

 Get a bunch of IP addresses using macvlan to avoid port conflicts on the same machine.

```bash
docker network create -d macvlan --subnet=10.10.0.0/18 --ip-range=10.10.10.0/24 --gateway=10.10.1.1 -o parent=eth0 pub
for n in {0..2}; do
  docker run --net pub --name es$n --ip 10.10.10.6$n -it docker.elastic.co/elasticsearch/elasticsearch:8.3.3
done
```

## tar

### tar with zstd compression algorithm

```bash
tar caf $Tarball.tzst $Directory
```

GNU tar 1.34: 8.1.1 Creating and Reading Compressed Archives  
https://www.gnu.org/software/tar/manual/html_node/gzip.html

Arch Linux - News: Now using Zstandard instead of xz for package compression  
https://archlinux.org/news/now-using-zstandard-instead-of-xz-for-package-compression/

Zstandard - Real-time data compression algorithm  
https://facebook.github.io/zstd/

Comparison of Compression Algorithms - LinuxReviews  
https://linuxreviews.org/Comparison_of_Compression_Algorithms
