# homework_10 #
## explanation 

## steps
    
    1. fork the repository and by using git clone command clone the repository to local machine 
    2. start the docker 
  
## setup
 
   1. use the following command to setup docker compose up --build
   2. use localhost/docs/ to open event management
   3. use localhost:5050 to open pgAdmin

## Assignment steps
  
   1. docker compose exec fastapi pytest to run pytest
   2. login to pgAdmin 
   3. using the command docker compose exec fastapi alembic upgrade head to upgrade 
   4. In pgAdmin we get users table 

## issues
   
   1. In repository add an issue that you found and create issue and make that as branch 
   2. use the following commands
       git fetch origin
       git checkout 1-issue1-in-register-and-login
   3. you have switched the branch
   4. Issue1 : https://github.com/rajasree9/event_manager/commit/869f33a5ccb583e9bb4280398e36151d83499ca6
               sa.Column('is_professional', sa.Boolean(), nullable=True, default=False),
               sa.Column('professional_status_updated_at', sa.DateTime(timezone=True), server_default=sa.text('now()'), nullable=True),
               sa.Column('role', sa.Enum('ADMIN', 'USER', 'PRO', 'ANONYMOUS', name='userrole'), nullable=False),

      after making changes in code save and run pytest
      use command docker compose exec fastapi alembic upgrade head
      refresh the pgAdmin page
      refresh event management page 
      authorize using username : admin
                      password : secret
      now in register click on try it out and also in login now you will see successfull responses
      Both the username and password should be same
      use command git add .
      and commit the changes and then push the changes to git hub
      we get a pull request merge the pull request issue is solved 

   5. Issue2 : https://github.com/rajasree9/event_manager/commit/77703a80357bc566320da7baff978466c38ce194
               full_name=user.full_name,
               bio=user.bio,
               profile_picture_url=user.profile_picture_url,
      At first these three values would be null so we make changes to the code to have these values 
      use command git add .
      and commit the changes and then push the changes to git hub
      we get a pull request merge the pull request issue is solved 
   
   6. Issue3 : https://github.com/rajasree9/event_manager/commit/019584ce545551af2bc9075f2a3fc54dc2a7b2d8
               profile_picture_url: Optional[str]

               the datatype of url is blocking the update so we change the datatype so that the update user id works correctly  
               use command git add .
               and commit the changes and then push the changes to git hub
               we get a pull request merge the pull request issue is solved
  7. Issue4 : https://github.com/rajasree9/event_manager/commit/fa0c13f725ebb7c4ad2ae9a673388c6ac223fc85
              if user already exists it gives bad request
               existing_email = await UserService.get_by_username(db, user.email)
              if existing_email:
               raise HTTPException(status_code=status.HTTP_400_BAD_REQUEST, detail="Email ID already exists")
 8. Issue5 : https://github.com/rajasree9/event_manager/commit/96b21834baed72673f157c715a2b0314d3cdcafc
             made changes to role
             role: Mapped[UserRole] = Column(SQLAlchemyEnum(UserRole), default=UserRole.USER, nullable=False)

# Docker 
https://hub.docker.com/repository/docker/rajasree961527/homework10/general

From this assignment, I gained valuable insights into both technical skills and collaborative processes. On the technical side, I honed my ability to work with Python and FastAPI to manage user data, including validating usernames and passwords, handling user roles, and managing user records such as creating, updating, and retrieving user information. By working with data models and incorporating Pydantic for data validation, I learned how to efficiently and effectively handle data integrity while ensuring a secure and consistent user experience. Additionally, implementing role-based access control and ensuring proper validation of user input reinforced best practices in security and application design. I faced various challenges, such as ensuring consistent validation rules for usernames and passwords and handling different user roles in a seamless manner.This iterative process taught me the importance of careful planning and attention to detail in application development. Overall, this assignment reinforced the importance of both technical expertise and collaboration in software development projects.
 
