# Tips
## 1. Android AudioTrack 播放声音结束 
### AudioPlayer.java

                        audioTrack.write(tempData, 0, tempData.length);
                        audioTrack.setNotificationMarkerPosition(audioTrack.getPlaybackHeadPosition() + tempData.length);
                        audioTrack.setPlaybackPositionUpdateListener(new AudioTrack.OnPlaybackPositionUpdateListener() {
                                @Override
                                public void onPeriodicNotification(AudioTrack track) {
                                    // nothing to do
                                }

                                @Override
                                public void onMarkerReached(AudioTrack track) {
                                    if (audioQueue.isEmpty()) {
                                        Log.d(TAG, "------Audio track end of file reached...");
                                        stop();
                                    }
                                }
                            });

