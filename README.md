# 250602-DEX401
Touch point for students of June Mulesoft Fundamentals

DEX401 - Anypoiont Development Fundamentals Classroom Reference - 250602 - PDT

Vincent Lowe
agentv@gmail.com
-------------------------------------------------------------------------------------------------------------------
Trailhead Academy:						https://trailheadacademy.salesforce.com/my-learning

Attendance Code:							YHE2L5

Salesforce Mimeo:							https://salesforce.mimeo.digital/MuleSoft

eBook Redemption Key:					USR81EXDW4WM

-------------------------------------------------------------------------------------------------------------------
Survey Link:									https://www.research.net/r/trailheadacademy

Survey ID:										survey ID

-------------------------------------------------------------------------------------------------------------------
[Zoom Link:](https://salesforce-training.zoom.us/j/83922746989?pwd=h3Vo1DbwbQOzFnuHX8jgbOu9ysXTbt.1)
Meeting ID: 83922746989

Class System Setup (pre-class): https://trailhead.salesforce.com/help?article=Computer-Setup-Guide-for-MuleSoft-Expert-Led-Classes#DEX401

Advanced REST Client: https://github.com/advanced-rest-client/arc-electron/releases/tag/v17.0.9

Postman: https://www.postman.com/downloads/

Help: https://help.mulesoft.com/

Docs: https://docs.mulesoft.com

Log Analyzer Tool: https://help.mulesoft.com/s/article/Support-Log-file-analyzer-tool

Status: https://status.mulesoft.com 
   
------------------------------------------------------------------------------
Java VM: https://docs.mulesoft.com/general/java-support

MuleSoft Pricing & Support: https://www.mulesoft.com/anypoint-pricing

Einstein for Anypoint Code Builder: https://videos.mulesoft.com/watch/Z3Xzk8RFds5erbzLASev1W

Log Analyzer: https://help.salesforce.com/s/articleView?language=en_US&id=Support-Log-file-analyzer-tool&type=1

------------------------------------------------------------------------------
https://anypoint.mulesoft.com
https://anypoint.mulesoft.com/exchange/?view=grid&type=app

-------------------------------------------------------------------------------------------------------------------
Classroom Playlist
-------------------------------------------------------------------------------------------------------------------
|Track Title|Artist|Notes|
|-----------|------|-----|
|Taxi (theme song)|Bob James||
|Smooth Criminal|Luca Stricagnoli||
|Blackbird|The Beatles||
|The Hitter|Mark Erelli|Mark wrote this song about his son|
|Ain't Misbehaving|Leon Redbone||
|Here We Go Again|Ray Charles and Norah Jones|Genius Loves Company|
|Sanford and Son TV Theme|Quincy Jones||
|Dos Oruguitas|Steven Joseph||


-------------------------------------------------------------------------------------------------------------------
Classroom Playlist
-------------------------------------------------------------------------------------------------------------------
	<flow name="getFlightsByID" doc:id="249479c9-b658-47ae-b3c6-626796c9a54c" >
		<http:listener doc:name="GET /flights/{ID}" doc:id="c96e4c7e-dc10-412a-be98-1617bdccd118" config-ref="American_API_Listener_config" path="/flights/{ID}" />
		<db:select doc:name="Select" doc:id="a7c0199e-330f-46c5-a9f3-8003d24ceb7b" config-ref="Database_Config" >
			<db:sql ><![CDATA[SELECT * FROM american
WHERE ID = :RID]]></db:sql>
			<db:input-parameters ><![CDATA[#[{RID: attributes.uriParams.ID}]]]></db:input-parameters>
		</db:select>
		<ee:transform doc:name="to JSON" doc:id="1f3ee3a2-960c-4518-9e2c-43ab4c46908a" >
			<ee:message >
				<ee:set-payload ><![CDATA[%dw 2.0
output application/json
---
payload map ( payload01 , indexOfPayload01 ) -> {
	ID: payload01.ID,
	code: (payload01.code1 default "") ++ (payload01.code2 default ""),
	price: payload01.price default 0,
	departureDate: payload01.takeOffDate as String default "",
	origin: payload01.fromAirport default "",
	destination: payload01.toAirport default "",
	emptySeats: payload01.seatsAvailable default 0,
	plane: {
		"type": payload01.planeType default "",
		totalSeats: payload01.totalSeats default 0
	}
}]]></ee:set-payload>
			</ee:message>
		</ee:transform>
	</flow>
