               
### Types of 3Ds
                    
3D Type | Description | Note | Accepting
------------- | ------------- | ------------- | -------------
**`Y`** | Authentication successful  |	Cardholder passed authentication | **YES**
`A` | Authentication attempted   |	Liability shift in most cases | NO
`N` | Authentication failed      |	Cardholder failed authentication | NO
`U` | Authentication unavailable |	No liability shift | NO
`E` | Error | No liability shift | NO


## Statuses in verify_info block

**Main statuses to check**

* bank_processing_state

* indacoin_main_status

**Ranking in descending order of importance of statuses**

1. bank_processing_state
2. indacoin_main_status: 
3. kyc_main_status

If both of __bank_processing_state__ and __indacoin_main_status__ are in completed state that means that payment should be processed soon.

If one of __bank_processing_state__ or __indacoin_main_status__ are in declined state that means that payment should be declined soon.

**Description of each status**

indacoin_main_status:

	ErrorDeclinedOnCompleating (declined),
	ErrorResponse (declined),
	Error (declined),
	NotPaid (declined),
	Declined (declined),
	PendingDecline (declined),
	WaitingToDecline (declined),
	Hold (neutral),
	WaitingToComplete (neutral),
	PendingComplete (neutral),
	Completed (completed)
  
indacoin_extra_status:

	CanceledDueToTimeout,
	FraudFound,
	FraudSuspect,
	UserDecline,
	VerificationTimeout,
	OtherDeclineReason,
	NotSet,
	VideoVerified,
	AutoComplete
  
kyc_main_status:

	UNKNOWN(neutral),
	VERIFIED(completed),
	REJECTED(declined),
	VERIFYING(neutral)
  
kyc_processing_state:

	unknown,
	init,
	pending,
	queued,
	awaitingUser,
	completed,
	completedSent,
	completedSentFailure
  
kyc_review_reject_type:

	UNKNOWN,
	FINAL,
	RETRY,
	EXTERNAL
  
kyc_docs_loaded:

	true,
	false
  
kyc_reject_labels: text field

bank_processing_state:

	FraudFails (declined),
	Error (declined),
	Chargeback (declined),
	Declined (declined),
	Hold (neutral),
	Completed (completed),
	CompletedAndSettleNeedToBeSend (neutral),
	CompletedAndSettleSent (neutral)
  
bank_reason: text field
