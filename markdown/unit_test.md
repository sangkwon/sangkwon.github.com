### 테스트 콘솔 명령어들
	./gradlew test -i    : 실제로 테스트 수행. verbose
	./gradlew clean build -x test
	./gradlew jTR : jacoco report 테스트케이스 실패시에도 나오도록


### Robolectric 사용

	Context context = Robolectric.application.getApplicationContext();
	context = Robolectric.buildActivity(Activity.class).create().get();
