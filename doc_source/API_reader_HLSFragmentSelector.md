# HLSFragmentSelector<a name="API_reader_HLSFragmentSelector"></a>

Contains the range of timestamps for the requested media, and the source of the timestamps\.

## Contents<a name="API_reader_HLSFragmentSelector_Contents"></a>

 **FragmentSelectorType**   <a name="KinesisVideo-Type-reader_HLSFragmentSelector-FragmentSelectorType"></a>
The source of the timestamps for the requested media\.  
When `FragmentSelectorType` is set to `PRODUCER_TIMESTAMP` and [GetHLSStreamingSessionURL:PlaybackMode](API_reader_GetHLSStreamingSessionURL.md#KinesisVideo-reader_GetHLSStreamingSessionURL-request-PlaybackMode) is `ON_DEMAND`, the first fragment ingested with a producer timestamp within the specified [FragmentSelector:TimestampRange](API_reader_FragmentSelector.md#KinesisVideo-Type-reader_FragmentSelector-TimestampRange) is included in the media playlist\. In addition, the fragments with producer timestamps within the `TimestampRange` ingested immediately following the first fragment \(up to the [GetHLSStreamingSessionURL:MaxMediaPlaylistFragmentResults](API_reader_GetHLSStreamingSessionURL.md#KinesisVideo-reader_GetHLSStreamingSessionURL-request-MaxMediaPlaylistFragmentResults) value\) are included\.   
Fragments that have duplicate producer timestamps are deduplicated\. This means that if producers are producing a stream of fragments with producer timestamps that are approximately equal to the true clock time, the HLS media playlists will contain all of the fragments within the requested timestamp range\. If some fragments are ingested within the same time range and very different points in time, only the oldest ingested collection of fragments are returned\.  
When `FragmentSelectorType` is set to `PRODUCER_TIMESTAMP` and [GetHLSStreamingSessionURL:PlaybackMode](API_reader_GetHLSStreamingSessionURL.md#KinesisVideo-reader_GetHLSStreamingSessionURL-request-PlaybackMode) is `LIVE`, the producer timestamps are used in the MP4 fragments and for deduplication\. But the most recently ingested fragments based on server timestamps are included in the HLS media playlist\. This means that even if fragments ingested in the past have producer timestamps with values now, they are not included in the HLS media playlist\.  
The default is `SERVER_TIMESTAMP`\.  
Type: String  
Valid Values:` PRODUCER_TIMESTAMP | SERVER_TIMESTAMP`   
Required: No

 **TimestampRange**   <a name="KinesisVideo-Type-reader_HLSFragmentSelector-TimestampRange"></a>
The start and end of the timestamp range for the requested media\.  
This value should not be present if `PlaybackType` is `LIVE`\.  
Type: [HLSTimestampRange](API_reader_HLSTimestampRange.md) object  
Required: No

## See Also<a name="API_reader_HLSFragmentSelector_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/kinesis-video-reader-data-2017-09-30/HLSFragmentSelector) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/kinesis-video-reader-data-2017-09-30/HLSFragmentSelector) 
+  [AWS SDK for Go \- Pilot](https://docs.aws.amazon.com/goto/SdkForGoPilot/kinesis-video-reader-data-2017-09-30/HLSFragmentSelector) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/kinesis-video-reader-data-2017-09-30/HLSFragmentSelector) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/kinesis-video-reader-data-2017-09-30/HLSFragmentSelector) 