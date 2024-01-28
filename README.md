# java_11_api
package ch11_java_api;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Calendar;
import java.util.Date;
import java.util.Locale;
import java.util.TimeZone;

public class ApiDate {

	public static void main(String[] args) {
		// 1.Date 클래스
		// 1970년 1월 1일 자정(UTC)이후의 시간을 밀리초 단위로 표현
		Date datetoDay = new Date();
		System.out.println(datetoDay);
		SimpleDateFormat sdf = new SimpleDateFormat("yyyy년 MM월 dd일 HH시 mm분 ss초");
		String strToday = sdf.format(datetoDay);
		System.out.println(strToday);
		// dateToday 사용하여 2024-01-17을 출력하시오
		SimpleDateFormat sdf2 = new SimpleDateFormat("yyyy-mm-dd");
		System.out.println(sdf2.format(datetoDay));
		// 뉴욕시간
		SimpleDateFormat sdf3 = new SimpleDateFormat("yyyy/MMdd HH:ss", Locale.US);
		TimeZone timeZone = TimeZone.getTimeZone("America/New_York");
		sdf3.setTimeZone(timeZone);
		String newYork = sdf3.format(datetoDay);
		System.out.println(newYork);

		String strDinner = "2024/0118 18:10:00";
		sdf = new SimpleDateFormat("yyyy/MMdd HH:ss");
		Date dinner = null;
		try {
			dinner = sdf.parse(strDinner);
		} catch (ParseException e) {
			e.printStackTrace();
		} finally {
			System.out.println(dinner);
		}
		//
		System.out.println(datetoDay.getTime());
		System.out.println(dinner.getTime());
		long diffMillSec = dinner.getTime() - datetoDay.getTime();
		System.out.println(diffMillSec + "밀리초 남음");
		System.out.println((diffMillSec / 1000) + "초 남음");
		System.out.println((diffMillSec / 1000 / 60) + "분 남음");
		System.out.println((diffMillSec / 1000 / 60 / 60) + "시간 남음");
		// Calendar 클래스 (YEAR, MONTH.. 같은 필드를 제공) 날짜계산 조작 유용함.
		// 1일뒤 한달 뒤 와 같은..
		Calendar calToday = Calendar.getInstance();
		System.out.println(calToday.getTime());
		System.out.println(calToday.get(Calendar.YEAR));
		System.out.println(calToday.get(Calendar.MONTH) + 1);
		System.out.println(calToday.get(Calendar.DATE));
		System.out.println(calToday.get(Calendar.HOUR_OF_DAY));
		// 3일뒤
		calToday.add(Calendar.DATE, 3);
		System.out.println(sdf.format(calToday.getTime()));
		// 10일전
		calToday.add(Calendar.DATE, -10);
		System.out.println(sdf.format(calToday.getTime()));
		// 5개월뒤
		calToday.add(Calendar.MONTH, 5);
		System.out.println(sdf.format(calToday.getTime()));
		// 달력만들기
		Calendar calendars = Calendar.getInstance();
		int year = 2024;
		int month = 1;
		calendars.set(year, month - 1, 1); // 해당월 1일날짜
		// 해당월의 마지막 일자 얻기
		int lastDay = calendars.getActualMaximum(Calendar.DAY_OF_MONTH);
		System.out.println(lastDay);
		// 해당 월의 시작요일
		// 1:일요일, 2:월요일....
		int startDay = calendars.get(Calendar.DAY_OF_WEEK);
		System.out.println(startDay);
		System.out.println(year + "년" + month + "월 달력");
		System.out.println("일\t월\t화\t수\t목\t금\t토");
		int current = 1;
		for (int i = 0; i <= 42; i++) {
			if (i < startDay) {
				System.out.printf("\t", current);
			} else {
				System.out.printf("%d\t", current);
				current++;
				if (current > lastDay) {
					break;
				}
			}
			if (i % 7 == 0) {
				System.out.println();
			}
		}
		//년, 월을 입력받아 해당 년월의 달력을 출력하는 기능을 구현하세요
//		workingCalendar(2024,2);
//		workingCalendar(2024,3);
//		workingCalendar(2024,4);
	//	workingCalendar(2024,5);
		
		Calendar workingCalendar = Calendar.getInstance();
		workingCalendar.set(year, month - 1, 1);
		
		
package ch11_java_api;



import java.text.DecimalFormat;



public class ApiFormat {



	public static void main(String[] args) {

		//숫자 형식 DecimalFormat

		//자리수에 맞춰 숫자 앞에 0붙이기 (코드값 필요할 때 사용)

		DecimalFormat format = new DecimalFormat("00000");

		System.out.println(format.format(1));

		System.out.println(format.format(1123));

		System.out.println(format.format(99999));

		//소수 뒤에 0붙이기

		DecimalFormat format2 = new DecimalFormat("0.000");

		System.out.println(format2.format(12.1));

		System.out.println(format2.format(12.12));

		//천 단위마다, 붙이기

		DecimalFormat format3 = new DecimalFormat("0,000");

		System.out.println(format3.format(1000000));

		System.out.println(format3.format(123400000));

	

	

	

	

	

	

	}



}

package ch11_java_api;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashMap;
import java.util.Random;
import java.util.Set;

public class ApiMath {

	public static void main(String[] args) {
		//Math
		//수학에서 사용되는 여러가지 함수들을 메서드로 제공하는 클래스
		final double PI=3.141592;
		//반올림 round
		long roundPI = Math.round(PI);
		System.out.println(roundPI);
		//소수 넷째 자리에서 반올림
		double fourPI = (Math.round(PI * 1000)) / 1000.0;
		System.out.println(fourPI);
		//올림 ceil
		double ceilPI =Math.ceil(PI);
		System.out.println(ceilPI);
		//내림 floor
		double flooPI = Math.floor(PI);
		System.out.println(flooPI);
		//절대값 abs
		int minus =-10;
		System.out.println(Math.abs(minus));
		//제곱 3의 4제곱 pow
		double powVal =Math.pow(3, 4);
		System.out.println(powVal);
		//제곱근(루트)
		System.out.println(Math.sqrt(4));
		//랜덤 숫자(난수) 생성
		//0~1 사이 실수 리턴(0포함, 1포함하지 않음)
		for(int i=0; i<100; i++) {
			System.out.println(Math.random());
		}
		
		//1~45
		int lotto = (int) (Math.random() * 45) + 1;
		System.out.println(lotto);
		//10~20 랜덤숫자
		int ranNum = (int) (Math.random( )* 11) + 10;
		System.out.println(ranNum);
		
		ArrayList<String> calssMateList = new ArrayList<>(Arrays.asList(
				                   "강성준","권보성","권유빈","김기찬","김대영","김동우",
				                   "김동현","김명기","김영주","김유정","김은혜","김휘건",
				                   "나항진","문성민","박진기","백현진","오정연","유하영",
				                   "이예진","이용빈","정유진"
	HashMap<String, String>	resultHashMap = randomGame(classMateList);
				                   Set<String> keySet = result.keySet();
				                   for(String key=keySet) {
				                	   System.out.println(key + "님은" + result)
				                   }
				)
				
				
				
				
				
	}

	public static String randomCard() {
		String result = null;
		// Random은 class로도 존재함.
		Random random = new Random();
		// 1~100 사이의 정수
		int num = random.nextInt(100) + 1;
		System.out.println(num);
		// 10% 확률 당첨
		if (num <= 10) {
			result = "당첨";
		} else {
			result = "꽝";
		}

		return result;
	}

	public static HashMap<String, String> randomGame(ArrayList<String> arr){
		HashMap<String, String> resultMap new HashMap<>();
		//input으로 입력받은 arr만큼
		for(int i=0; i <arr.size(); i++) {
			//key:학생이름, value:당첨or꽝
			resultMap.put(arr.get(i), randomCard());
		}
		return resultMap;
	}

}
package ch11_java_api;



public class ApiStringBuffer {



	public static void main(String[] args) {

		

		

		String a ="길동";

		System.out.println(a.hashCode());

		a="팽수";

		System.out.println(a.hashCode());

		//java에서 불면(immutable) 가변(mutable)

		//불변변수는 한 번 초기화되면 그 값이 변경되지 않음.

		//String은 불변

		

		//가변변수는 선언된 후에도 그 값이 변경될 수 있음.

		//int, ArrayList... 가변 변수

        //String은 불변객체로 값을 계속 수정하게 되면

		//메모리 영역에 매번 새로운 String 객체가 만들어지고 그로인해 가비지컬렉터(메모리관리)

		//에서 할일이 많아짐(비효율적)

		//그래서 변경이 만다는 StringBuffer 클래스 사용

		

		StringBuffer strBuffer = new StringBuffer();

		strBuffer.append("hi");

		System.out.println(strBuffer);

		strBuffer.append(" hello");

		System.out.println(strBuffer);

		//문자열 가져오기

		String str = strBuffer.toString();

		System.out.println(str);

		

	

	

	

	}



}

package ch11_java_api;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.ObjectInputStream.GetField;
import java.net.URL;

import javax.net.ssl.HttpsURLConnection;

import org.json.simple.JSONArray;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;
import org.json.simple.parser.ParseException;

public class ApjJson {

	public static void main(String[] args) throws IOException, ParseException {

		String allUrl = "https://api.upbit.com/v1/market/all";
		// URL클래스 사용 요청
		URL url = new URL(allUrl);
		HttpsURLConnection conn = (HttpsURLConnection) url.openConnection();
		// 요청방식 설정(get or post)
		conn.setRequestMethod("GET");
		// 연경 타임아웃설정
		conn.setReadTimeout(5000); // 5초
		conn.setDoOutput(true);
		int resCode = conn.getResponseCode(); // 응답에 따른 요청코드 리턴 200 정상
		// 정상응답일때 처리
		if (resCode == HttpsURLConnection.HTTP_OK) {
			System.out.println(resCode);
			BufferedReader in = new BufferedReader(new InputStreamReader(conn.getInputStream()));
			String inputLine;
			StringBuffer response = new StringBuffer();
			// 내용일 없을떄 까지 버퍼에 담기
			while ((inputLine = in.readLine()) != null) {
				response.append(inputLine);
			}
			in.close();
			System.out.println(response.toString());
			JSONParser parser = new JSONParser();
			// 응답데이터의 구조가 처음배열
			// Json데이터 형태로 문자열을 파싱(json데이터 규칙으로 읽어드림
			JSONArray jsonArray = (JSONArray) parser.parse(response.toString());
			for (Object object : jsonArray) {
				// 응답데이터의 구조가 배열안에 객체 (key:value)형태로 담겨있음
				JSONObject jsonObj = (JSONObject) object;
				System.out.println("market:" + jsonObj.get("market"));
				System.out.println("kor:" + jsonObj.get("korean_name"));
				System.out.println("en:" + jsonObj.get("english_name"));
			}

		}

	}
	public static JSONObject getCoin(String code) {
		JSONObject obj = null;
		String detailUrl = "https://api.upbit.com/vl/ticker?markets="+code;
		//
		return obj;
	}

}



		
