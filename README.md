# react-video-status-zw
显示和控制多通道视频播放，包含进度，速度，时分秒切换，向前向后播放功能
* 安装方式<br>
npm install react-video-status-zw <br>
* 代码示例<br>
```
import React, { Component } from 'react';
import VideoStatus from 'react-video-status-zw';

class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      playingStatus: '',
      direction: 'forward',
    };
  }

  startPaly=() => {
    this.setState({
      playingStatus: 'start',
    });
  }

  stopPaly=() => {
    this.setState({
      playingStatus: 'stop',
    });
  }

  pausePaly=() => {
    this.setState({
      playingStatus: 'pause',
    });
  }

  continuePaly=() => {
    this.setState({
      playingStatus: 'continue',
    });
  }

  playForward=() => {
    this.setState({
      direction: 'forward',
    });
  }

  playBackward=() => {
    this.setState({
      direction: 'backward',
    });
  }

  render() {
    const { playingStatus, direction } = this.state;
    return (
      <div style={{ width: '80%', height: '100%', margin: 'auto' }}>
        <div>
          <VideoStatus
            channels={[1, 3, 5]}
            channelData={{
              1: [
                {
                  ID: 1, DisplayText: '', StationId: 1, StartTime: '2018-06-10 10:00:00', EndTime: '2018-06-10 11:36:00',
                },
                {
                  ID: 2, DisplayText: '', StationId: 1, StartTime: '2018-06-10 15:00:00', EndTime: '2018-06-10 15:37:23',
                },
              ],
              3: [
                {
                  ID: 3, DisplayText: '', StationId: 5, StartTime: '2018-06-10 5:55:55', EndTime: '2018-06-10 09:36:30',
                },
                {
                  ID: 4, DisplayText: '', StationId: 5, StartTime: '2018-06-10 20:00:00', EndTime: '2018-06-10 22:37:23',
                },
              ],
            }}
            playingStatus={playingStatus}
            direction={direction}
            interval={100}
          />
        </div>
        <hr />
        <div>
          <button type="button" onClick={this.startPaly} style={{ marginLeft: 10 }}>开始播放</button>
          <button type="button" onClick={this.stopPaly} style={{ marginLeft: 10 }}>停止播放</button>
          <button type="button" onClick={this.pausePaly} style={{ marginLeft: 10 }}>暂停播放</button>
          <button type="button" onClick={this.continuePaly} style={{ marginLeft: 10 }}>继续播放</button>
          <button type="button" onClick={this.playForward} style={{ marginLeft: 10 }}>向前播放</button>
          <button type="button" onClick={this.playBackward} style={{ marginLeft: 10 }}>向后播放</button>
        </div>
      </div>
    );
  }
}
ReactDOM.render(<App />, document.getElementById('root'));
```
* 配置项 options<br>

名称|类型|必填|含义
--|:--:|--:|--:
channels|array|yes|视频通道号数组
channelData|object|yes|视频数据
playingStatus|string|yes|播放状态start,pause,stop,continue
direction|string|no|播放方向，正常播放 forward，后退 backward
interval|number|no|播放速度、时间间隔


