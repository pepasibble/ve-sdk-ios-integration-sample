# Banuba VideoEditor SDK
##  RecordButtonProvider

To implement your own custom record button, create a provider which returns your custom view:

``` swift
/// The record button view provider.
public protocol RecordButtonProvider {
  func getButton() -> RecordButton
}
``` 

This provider should be assigned to the [`recordButtonProvider`](camera_styles.md#L30) property of a `RecorderConfiguration` struct.

Your custom record button should implement the `RecordButton` protocol:

``` swift
public protocol RecordButton: UIView {
  var delegate: RecordButtonDelegate? { get set }
  var configuration: RecordButtonConfiguration? { get set }
  func updateVideoRecordingProgress(_ progress: Double)
  func changeViewToIdleState()
  func changeViewToRecordingState()
  func reset()
}

public protocol RecordButtonDelegate: AnyObject {
  func recordButtonDidTakePhoto(_ recordButton: RecordButton)
  func recordButtonDidStartVideoRecording(_ recordButton: RecordButton)
  func recordButtonDidStopVideoRecording(_ recordButton: RecordButton)
}
``` 
