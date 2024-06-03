School Contract
This Solidity contract represents a simple school system where the owner of the contract can add, update, and retrieve information about students enrolled in the school.
This code basically shows the use of Revert(), Require(), and Assert() which are usually error handling method in solidity.

Features
Add Student: The contract owner can add a new student by providing their ID, name, age, and grade. The age must be between 5 and 18, and the grade must be between 1 and 12.
Update Student: The contract owner can update the details of an existing student, including their name, age, and grade.
Get Student Information: Anyone can retrieve the information of a student by providing their ID.
Total Students: Anyone can check the total number of students enrolled in the school.
Usage
Deploy the Contract: Deploy the contract on the Ethereum network using Remix or any other Solidity IDE.

Add Students: Once deployed, the contract owner can add students by calling the addStudent function with the required parameters: ID, name, age, and grade.

Update Student Information: The contract owner can update the information of existing students using the updateStudent function.

Retrieve Student Information: Anyone can retrieve the details of a student by calling the getStudent function with the student's ID.

Check Total Students: Anyone can check the total number of students enrolled in the school by calling the totalStudents function.

CODE(methods):
 function addStudent(uint256 _id, string memory _name, uint256 _age, uint256 _grade) public onlyOwner {
        require(_age >= 5 && _age <= 18, "Age must be between 5 and 18");
        require(_grade >= 1 && _grade <= 12, "Grade must be between 1 and 12");

        students[_id] = Student(_id, _name, _age, _grade);
        studentCount++;

        emit StudentAdded(_id, _name, _age, _grade);
    }

    and
function updateStudent(uint256 _id, string memory _name, uint256 _age, uint256 _grade) public onlyOwner {
        require(_age >= 5 && _age <= 18, "Age must be between 5 and 18");
        require(_grade >= 1 && _grade <= 12, "Grade must be between 1 and 12");

        Student storage student = students[_id];
        if (bytes(student.name).length == 0) {
            revert("Student does not exist");
        }

        student.name = _name;
        student.age = _age;
        student.grade = _grade;

        emit StudentUpdated(_id, _name, _age, _grade);
    }



License
This contract is released under the MIT License. See the LICENSE file for more details.

