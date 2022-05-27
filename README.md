1. add following to application.properties

        spring.datasource.url=jdbc:mysql://localhost/test
        spring.datasource.username=root
        spring.datasource.password=1234        
        spring.datasource.driverClassName=com.mysql.jdbc.Driver        
        spring.flyway.baselineOnMigrate = true

2. Add following to the pom.xml

		<dependency>
			<groupId>org.flywaydb</groupId>
			<artifactId>flyway-mysql</artifactId>
		</dependency>
		
		<dependency>
        	<groupId>org.flywaydb</groupId>
        	<artifactId>flyway-core</artifactId>
        </dependency>
        
3. File name formate under `src/main/resource/db/migration

        <Prefix><Version>__<Description>.sql
        V1__init.sql

4. Sample migration script


        CREATE TABLE product(
            id SERIAL PRIMARY KEY ,
            name varchar(255),
            price double precision
        );
        
5. If you do not want automatic db migration when running the application

        @Bean
        	public FlywayMigrationStrategy flywayMigrationStrategy(){
        		return args ->{};
        	}                
        