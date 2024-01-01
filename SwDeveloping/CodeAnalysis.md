# Table of Contents

- [Table of Contents](#table-of-contents)
  - [cppcheck](#cppcheck)
  - [tessy](#tessy)
  - [Polyspace](#polyspace)
  - [pclint](#pclint)
  - [perf](#perf)
    - [What is it](#what-is-it)
    - [Installation](#installation)
    - [Usage](#usage)
  - [valgrind](#valgrind)
  - [clang static code analyzer](#clang-static-code-analyzer)
  - [Cyclomatic complexity](#cyclomatic-complexity)

## cppcheck

## tessy

## Polyspace

## pclint

## perf

[Examples of calling](https://www.brendangregg.com/perf.html)

### What is it

perf - Performance analysis tools for Linux

When an application encounters some performance issues, we have to find the code that causes the problem to optimize only what really matters.

To find the code we have to optimize, the profilers are really useful. In this post, we’ll use the Linux perf tools to profile a simple C++ application.

The perf tools are integrated in the Linux kernel since the 2.6 version. The perf tools are based on the perf events subsystem. The perf profiler uses hardware counters to profile the application. The result of this profiler are really precise and because it is not doing instrumentation of the code, it is really fast

### Installation

On Ubuntu, I install it with:

```shell
sudo apt-get install linux-tools-common linux-tools-generic linux-tools-`uname -r`
```

### Usage

To profile an application, you have to record information about an executation, for that, you just have to use perf record:

```shell
perf record program [program_options]
```

For example :

```shell
perf record sensReceiver
```

Once the execution is over, perf will gives you some information about the record, like:

```shell
[ perf record: Woken up 22 times to write data ]
[ perf record: Captured and wrote 5.755 MB perf.data (~251434 samples) ]
```

If you see that the size of the perf.data is really small, generally for small execution time, you can configure the event period in order to have more information with the –count=period option using a small period. I usually uses 1000, but it can be useful to use a smaller number when the application has a short execution time.

Then, to see the list of the most costly functions, you just have to use perf report :

```shell
perf report
```

It will display a list of the most costly functions ordered by cost. Here is an example taken from one of my C++ applications (the length of the function names is reduced to fit the screen) here :

```shell
 Samples: 150K of event 'cycles', Event count (approx.): 96633172578                                                                                  
36.62%  sensReceiver  libQtGui.so.4.8.4           [.] 0x0000000000205959
16.40%  sensReceiver  libc-2.17.so                [.] __memcpy_ssse3_back
 6.77%  sensReceiver  [kernel.kallsyms]           [k] 0xffffffff81043e6a
 4.67%  sensReceiver  libQtCore.so.4.8.4          [.] 0x00000000000bd47b
 1.44%  sensReceiver  libc-2.17.so                [.] _int_malloc
 1.38%  sensReceiver  libc-2.17.so                [.] _int_free
 1.02%  sensReceiver  libc-2.17.so                [.] malloc
 0.78%  sensReceiver  oxygen.so                   [.] 0x0000000000092d0c
 0.61%  sensReceiver  libQtCore.so.4.8.4          [.] QString::operator=(QString const&)
 0.49%  sensReceiver  libQtGui.so.4.8.4           [.] QWidgetPrivate::getOpaqueChildren() const
 0.39%  sensReceiver  sensReceiver                [.] QwtPolygonClipper<QPolygonF, QRectF, QPointF, double>::clipPolygon(QPolygonF const&, bool) con
 0.37%  sensReceiver  libQtGui.so.4.8.4           [.] QTextLine::layout_helper(int)
 0.35%  sensReceiver  libQtCore.so.4.8.4          [.] qdtoa(double, int, int, int*, int*, char**, char**)
 0.35%  sensReceiver  libQtCore.so.4.8.4          [.] QLocalePrivate::longLongToString(QChar, QChar, QChar, QChar, long long, int, int, int, unsigne
 0.34%  sensReceiver  sensReceiver                [.] QRectF qwtBoundingRectT<QPointF>(QwtSeriesData<QPointF> const&, int, int)
 0.34%  sensReceiver  libc-2.17.so                [.] free
 0.34%  sensReceiver  sensReceiver                [.] QwtPlotCurve::drawLines(QPainter*, QwtScaleMap const&, QwtScaleMap const&, QRectF const&, int,
 0.29%  sensReceiver  libc-2.17.so                [.] __memset_sse2
 0.28%  sensReceiver  libc-2.17.so                [.] realloc
 0.27%  sensReceiver  libQtGui.so.4.8.4           [.] QTextEngine::shapeTextWithHarfbuzz(int) const
 0.25%  sensReceiver  libc-2.17.so                [.] malloc_consolidate
 0.25%  sensReceiver  libQtGui.so.4.8.4           [.] QFont::toString() const
 0.21%  sensReceiver  libQtCore.so.4.8.4          [.] QCoreApplicationPrivate::sendThroughObjectEventFilters(QObject*, QEvent*)
 0.21%  sensReceiver  libQtGui.so.4.8.4           [.] QWidget::metric(QPaintDevice::PaintDeviceMetric) const
 0.21%  sensReceiver  sensReceiver                [.] QwtArraySeriesData<QPointF>::sample(unsigned long) const
 0.20%  sensReceiver  libc-2.17.so                [.] _int_realloc
 0.20%  sensReceiver  libQtGui.so.4.8.4           [.] QApplication::font()
```

For every functions, you have the information about the cost of the function, the command used to launch it and the shared object in which the function is located. You can navigate through the list like in more utility.

This tool can be really useful to see which functions is interesting to optimize in order to increase the overall performance of the application

## valgrind

Valgrind is an instrumentation framework for building dynamic analysis tools. There are Valgrind tools that can automatically detect many memory management and threading bugs, and profile your programs in detail.
memory profiling

Start it with:

```shell
valgrind --tool=memcheck program_name
```

For memory leaks detection start it with:

```shell
valgrind --tool=memcheck --leak-check=yes program_name
```

For further information read http://www.cprogramming.com/debugging/valgrind.html
profiling application with Callgrind / KCacheGrind

We have to start by profiling the application with Callgrind. To profile an application with Callgrind, you just have to prepend the Callgrind invocation in front of your normal program invocation:

```shell
valgrind --tool=callgrind program [program_options]
```

The result will be stored in a callgrind.out.XXX file where XXX will be the process identifier.

You can read this file using a text editor, but it won’t be very useful because it’s very cryptic. That’s here that KCacheGrind will be useful. You can launch KCacheGrind using command line or in the program menu if your system installed it here. Then, you have to open your profile file.

For further information read [Link](http://www.baptiste-wicht.com/2011/09/profile-c-application-with-callgrind-kcachegrind/)

From comments: I use "valgrind --tool=callgrind --dump-instr=yes --collect-jumps=yes ./program program_parameters", and then I can see function names in kcachegrind. Entry and exit parameters however..

## clang static code analyzer

Use it as

```shell
scan-build make
```

Default report stored in /tmp. Further information at [Link](http://clang-analyzer.llvm.org/scan-build.html)

## Cyclomatic complexity

Cyclomatic Complexity is a metric of complexity that counts the number of independent paths through the source code, and assigns a single numerical score for each method. [Link](http://gmetrics.sourceforge.net/gmetrics-CyclomaticComplexityMetric.html)

In Linux we have the pmccabe tool. I used it like:

```shell
pmccabe -vt *.c
```
