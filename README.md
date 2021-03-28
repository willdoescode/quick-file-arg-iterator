# quick-file-arg-iterator

## Adding to project

In project dir

```shell
git clone https://github.com/willdoescode/quick-file-arg-iterator.git
```

build.zig

```zig
exe.addPackage(.{
  .name = "args",
  .path = "./quick-file-arg-iterator/src/main.zig"
});
```

## Usage

```zig
const Args = @import("args").Args;

pub fn main() !void {
  const max_file_buf_size = 10_000;
  var args = Args.init(&std.process.args(), max_file_buf_size, &std.heap.page_allocator);
  defer args.deinit();

  while (args.next()) |content| doWhatever(content);
}
```
