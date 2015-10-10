##Latihan Hello World
----------------
** langkah 1 **
----------------
buat index.html
<html>
  <head>
    <title>Hello World</title>

    <!-- include react -->
    <script src="build/react.js"></script>

    <!-- diperlukan untuk bisa merender komponen mirip menulis HTML -->
    <script src="build/JSXTransformer.js"></script>

  </head>
  <body>

    <div id="mount-point"></div>

  </body>
</html>



----------------
** langkah 2 **
----------------

pada index.html, masukan script berikut pada head setelah script JSXTransformer

<script type="text/jsx">
  // buat komponen
  var Salam = React.createClass({
    render: function(){
      return (
        <span>
          {this.props.ucapan}
          <b> {this.props.kepada}</b>
        </span>
      );
    }
  });

  // render
  React.render(<Salam ucapan="Selamat Pagi" kepada="Azam"/>,
                document.getElementById('mount-point'));
</script>

----------------
** langkah 3 : Latihan *Event Handling* Komponen **
----------------

<script type="text/jsx">
  // buat komponen
  var Salam = React.createClass({
    handleClick: function(){
      alert('baru saja diklik');
    },
    render: function(){
      return (
        <span>
          {this.props.ucapan}
          <b onClick={this.handleClick}> {this.props.kepada}</b>
        </span>
      );
    }
  });

  // render
  React.render(<Salam ucapan="Selamat Pagi" kepada="Azam"/>,
                document.getElementById('mount-point'));
</script>


----------------
** langkah 4 : Latihan *State* Komponen **
----------------

<script type="text/jsx">
  // buat komponen
  var Salam = React.createClass({
    getInitialState: function(){
        return {
           background: '#fff'
        }
    },
    handleClick: function(){
        this.setState({background: '#0f0'})
    },
    render: function(){
      return (
        <span style={{background: this.state.background}}>
          {this.props.ucapan}
          <b onClick={this.handleClick}> {this.props.kepada}</b>
        </span>
      );
    }
  });

  // render
  React.render(<Salam ucapan="Selamat Pagi" kepada="Azam"/>,
                document.getElementById('mount-point'));
</script>


----------------
** langkah 5 : Latihan Siklus Komponen **
----------------

<script type="text/jsx">
  // buat komponen
  var Salam = React.createClass({
    getInitialState: function(){
        return {
           background: '#fff'
        }
    },
    componentDidMount: function(){
        alert('component baru saja dirender');
    },
    componentWillUnmount: function(){
        alert('component akan dihilangkan dari DOM');
    },
    handleClick: function(){
        this.setState({background: '#0f0'})
    },
    render: function(){
      return (
        <span style={{background: this.state.background}}>
          {this.props.ucapan}
          <b onClick={this.handleClick}> {this.props.kepada}</b>
        </span>
      );
    }
  });

  // render
  React.render(<Salam ucapan="Selamat Pagi" kepada="Azam"/>,
                document.getElementById('mount-point'));
</script>
