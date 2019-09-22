# Objecta


iOS Versions Supported: iOS 12.0 and above. Xcode Version Required: 10.0 and above

Overview

This is a camera app that continuously detects the objects (bounding boxes and classes) in the frames seen by your device's back camera, using a quantized MobileNet SSD model trained on the COCO dataset. These instructions walk you through building and running the demo on an iOS device.

The model files are downloaded via scripts in Xcode when you build and run. You don't need to do any steps to download TFLite models into the project explicitly.

Prerequisites

You must have Xcode installed

You must have a valid Apple Developer ID

The app requires a camera and must be executed on a real iOS device. You can build it and run with the iPhone Simulator but the app raises a camera not found exception.

You don't need to build the entire TensorFlow library to run the demo, it uses CocoaPods to download the TensorFlow Lite library.

You'll also need the Xcode command-line tools: xcode-select --install If this is a new install, you will need to run the Xcode application once to agree to the license before continuing.

Building the Object Detection App

Install CocoaPods if you don't have it. sudo gem install cocoapods

Install the pod to generate the workspace file: cd lite/examples/object_detection/ios/ pod install If you have installed this pod before and that command doesn't work, try pod update At the end of this step you should have a file called ObjectDetection.xcworkspace

Open ObjectDetection.xcworkspace in Xcode.

Please change the bundle identifier to a unique identifier and select your development team in 'General->Signing' before building the application if you are using an iOS device.

Build and run the app in Xcode. You'll have to grant permissions for the app to use the device's camera. Point the camera at various objects and enjoy seeing how the model classifies things!

Note

Please do not delete the empty references to the .tflite and .txt files after you clone the repo and open the project. These references will be fulfilled once the model and label files are downloaded when the application is built and run for the first time. If you delete the references to them, you can still find that the .tflite and .txt files are downloaded to the Model folder, the next time you build the application. You will have to add the references to these files in the bundle separately in that case.

Model Used

This app uses a MobileNet SSD model trained on COCO dataset. The input image size required is 300 X 300 X 3. You can download the model here. You can find more information on the research on object detection here.

iOS App Details

The app is written entirely in Swift and uses the TensorFlow Lite Swift library for performing image classification.

Note: Objective-C developers should use the TensorFlow Lite Objective-C library.

