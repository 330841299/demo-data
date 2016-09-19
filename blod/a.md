# 我是A.md
```js
import React, { PropTypes } from 'react';
import { getMd } from './utils/helpers';
import marked from  'marked';

class Blog extends React.Component {
    constructor(){
      super();
      this.state={
        data:'',
        wait:true
      }
    }
    componentDidMount(){
      let add = this.props.params.title
      console.log(this.props);
      getMd(add)
        .then( (recData) => {
          this.setState({
            data:recData.getMd,
            wait:false
          })
          // console.log(this.state.data);
        });
    }
  render () {
    // console.log(this.props);
    let content = this.state.wait? '请稍等' : marked(this.state.data)
    return(
      <div>
        <div dangerouslySetInnerHTML={{__html:content}}/>
      </div>
    )
  }
}

export default Blog;

```
