
----------------
** Langkah 2 : Buat index2.html **
----------------

<html>
  <head>
    <title>Hello World</title>
  </head>
  <body>
     <div id="mount-point"></div>
     <script src="js/bundle.js"></script>
  </body>
</html>


----------------
** Langkah 3 : Buat folder js, lalu difolder tersebut buat file Salam.react.js **
----------------
var React = require('react');

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

module.exports = Salam;


----------------
** Langkah 4 : Buat file app.js pada folder js **
----------------

var React = require('react');
var Salam = require('./Salam.react');

// render
React.render(<Salam ucapan="Selamat Siang" kepada="Azam"/>,
                document.getElementById('mount-point'));

----------------
** Langkah 5 : Buat bundle.js dengan perintah browserify **
----------------

browserify -t reactify js/app.js -o js/bundle.js
