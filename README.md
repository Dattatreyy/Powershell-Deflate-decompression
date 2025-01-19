# Powershell-Deflate-decompression
Script for decompressing a base64-encoded, deflate-compressed string in PowerShell.

```powershell
$deflateStream = New-Object IO.Compression.DeflateStream(
    [IO.MemoryStream]::new(
        [Convert]::FromBase64String(
            'NY8xb8IwEIX/yikLyWAHpKoDW5UOHSpAypAlUnHIlRjZPst3xOTfN7Tq+N7wve+1YpKoU6ILMkPR7PvOhpEy9+3CHeXXl//iRBlTO6Fz/bzT2z4+Mz+zxgcWoN7S9e4xyKdlgUJlmOw4YgCFEYYlmpWvAkVQDXlvwgjnwuIDyvKAWR2HG14E1lFBrw8ousOhcXblVfqdcnBkxlaSDddyM4lE3tc17vQ3WUczJrmnYFKys3GaJ4q1ifErYvKW2VJgfWMKm6o6F6vp36NWFofw8Sv5Aw=='
        )
    ),
    [IO.Compression.CompressionMode]::Decompress
)

$reader = New-Object System.IO.StreamReader($deflateStream, [Text.Encoding]::ASCII)
$decompressedData = $reader.ReadToEnd()

$decompressedData

```

Ref : https://www.cynet.com/attack-techniques-hands-on/powershell-obfuscation-demystified-series-chapter-2-concatenation-and-base64-encoding/
