# Key Management<a name="key-management"></a>

Amazon Transcribe works with AWS Key Management Service \(KMS\) to provide enhanced encryption for your data\. Amazon S3 already enables you to encrypt your input audio when creating a transcription job\. Integration with KMS enables you to encrypt the output of the [StartTranscriptionJob](API_StartTranscriptionJob.md) operation\. 

If you don't specify an encryption key, the output of the transcription job is encrypted with the default Amazon S3 key \(SSE\-S3\)\.

## KMS Encryption with the AWS Console<a name="kms-console"></a>

To encrypt the output of your transcription job, you can choose between using an encryption key for the account that is making the request, or you can use an encryption key from another account\.

If you don't specify an encryption key, the output of the transcription job is encrypted with the default Amazon S3 key \(SSE\-S3\)\.

**To enable output result encryption**

1. Under **Output data** choose **Encryption**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/transcribe/latest/dg/images/output-encryption.png)

1. Choose whether the KMS customer\-managed key \(CMK\) is from the account you're currently using or from a different account\. If you want to use a key from the current account, choose the key from **KMS key ID**\. If you're using a key from a different account, you need to enter the key's ARN\. To use a key from a different account, the caller must have `kms:Encrypt` permissions for the KMS key\.

## KMS Encryption with the API<a name="kms-api"></a>

To use output encryption with the API, you set the `OutputEncryptionKMSKeyId` parameter of the [StartTranscriptionJob](API_StartTranscriptionJob.md) operation\. You can use an encryption key from the current account, or you can use a key from another account\. The account that you are using to create the job must have `kms:Encrypt` permissions for the KMS key\.

You can use either of the following to identify a KMS key in the current account:
+ KMS Key ID: "1234abcd\-12ab\-34cd\-56ef\-1234567890ab"
+ KMS Key Alias: "alias/ExampleAlias"

You can use either of the following to identify a KMS key in the current account or another account:
+ Amazon Resource Name \(ARN\) of a KMS Key: "arn:aws:kms:region:account ID:key/1234abcd\-12ab\-34cd\-56ef\-1234567890ab"
+ ARN of a KMS Key Alias: "arn:aws:kms:region:account ID:alias/ExampleAlias"