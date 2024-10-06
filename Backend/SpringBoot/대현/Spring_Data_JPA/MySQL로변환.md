# JpaRepository<Entity, type> 쿼리메소드
- public List<Entity> findAllByScoreGreaterThanEqual(Entity)
   - findAll : 모든 데이터를 찾는다
   - Score : 어떠한 필드를
   - GreaterThanEqual : 기호 설정


# @Transient
- 엔티티 객체의 데이터와 테이블의 컬럼(column)과 매핑하고 있는 관계를 **제외**하기 위해 사용된다