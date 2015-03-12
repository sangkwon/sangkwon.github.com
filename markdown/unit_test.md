### 테스트 콘솔 명령어들
	./gradlew test -i    : 실제로 테스트 수행. verbose
	./gradlew clean build -x test
	./gradlew -Dtest.single=<MyTestClass> : 하나만 실행시키고자 할 때에. 결과는 레포트 파일에서
	./gradlew jTR : jacoco report 테스트케이스 실패시에도 나오도록

### Report 파일 위치
* Jacoco
	* <Module>/build/reports/jacoco/jacocoTestReport/html/index.html
	* Code coverage & branch coverage
* TestCase
	* <Module>/build/test-report/debug/index.html
	* Testcase success or fail

### Robolectric 사용
	Context context = Robolectric.application.getApplicationContext();
	context = Robolectric.buildActivity(Activity.class).create().get();
