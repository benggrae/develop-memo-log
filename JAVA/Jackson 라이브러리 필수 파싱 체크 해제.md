Jackson 라이브러리를 이용하여 파싱할 경우에 필수 값 체크가 기본값이다.
DTO 클래스인 경우에  옵션을 설정해줘야 필수 값 체크를 안한다.

* 필수값 체크리스트
	*  해당 키가 있을 경우?
	* 해당값이 공백일 경우 등 



* @JsonIgnoreProperties(ignoreUnknown = true)  해당 옵션을 주어 해결

```JAVA
  
@JsonIgnoreProperties(ignoreUnknown = true)  
public class VehiclesRequest {  
  
    //동화 기업 코드  
    private final static String DW_COMP_CD = "K100";  
    private final static String MLNG_KO_CD = "KO";  
  
    /**  
     * 차량번호     * */    private String carNo;  
  
    public void validate() {  
        if (StringUtil.isEmpty(carNo)) {  
            throw new IllegalArgumentException("자동차 번호는 필수입니다.");  
        }  
    }  
  
    public void setCarNo(String carNo) {  
        this.carNo = carNo;  
    }  
  
    public VhclMngmt toDbDto() {  
        VhclMngmt vhclMngmt = new VhclMngmt();  
        vhclMngmt.setCompCd(DW_COMP_CD);  
        vhclMngmt.setMlngCd(MLNG_KO_CD);  
        //차량번호  
        vhclMngmt.setVhclNo(carNo);  
        vhclMngmt.setUseYn("Y");  
        return vhclMngmt;  
    }  
}




```