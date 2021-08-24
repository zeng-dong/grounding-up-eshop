# PostgreSQL
1. docker image, add 
    discountdb:
        image: postgres
    into docker.compose.yml
2. add under volumes:
    postgres_data:
2. add discountdb under services in docker-compose.override.yml

# pgAdmin
1. add pgadmin into docker-compose
2. add volumes
3. add pgadmin service into docker-compose.override
4. docker-compose -f docker-compose.yml -f docker-compose.override.yml up -d
5. should see the container in Portainer
6. localhost:5050
7. use email and password defined in environment variables
8. click 'add server'
    8.1 server name: DiscountServer
    8.2 connection: 
        name: discountdb
        port: take the default 5432
        username: admin
        password: admin1234
    8.3 'save'
9. now can see DiscountServer in the left-hand browser pane under Servers node

# create coupon table using pgAdmin
1. Databases => Schemas => Tools => New Query Tool
2. script: CREATE TABLE Coupon(
		ID SERIAL PRIMARY KEY         NOT NULL,
		ProductName     VARCHAR(24) NOT NULL,
		Description     TEXT,
		Amount          INT
	);
3. execute
4. seed: INSERT INTO Coupon (ProductName, Description, Amount) VALUES ('IPhone X', 'IPhone Discount', 150);

    INSERT INTO Coupon (ProductName, Description, Amount) VALUES ('Samsung 10', 'Samsung Discount', 100);
5. execute
