## SaveMyAss(ignments) from Accidental Plagiarism

*SaveMyAss* is a little tool to address the following problem.

- **Instructors** often like to use a GitHub repository to share class materials, including assignments. This repository is public and is periodically updated.

- **Students** find it convenient to fork the repository in order to easily get the latest updates while being able to make and keep their own changes. *However, this is a problem when it comes to assignments!* Students may accidentally push their assignment solutions to their fork of the repository. Since the original repository is public, so is their fork &mdash; and so are their solutions! **This is accidental plagiarism.** The only way around this is to manage another way to store and manage their solutions.

*SaveMyAss* allows instructors to enable a simple mechanism to prevent students from accidentally plagiarizing their assignments. Instructors can specify which files are considered assignments, and students can run *SaveMyAss* to automatically encrypt these files before pushing them to their fork. **The solutions are still stored in the student's fork, but they are not visible in clear text!**

## Using SaveMyAss

### For Instructors

Instructors can provide *SaveMyAss* along with their repository to make it easy for students (and to encourage them) to use it. 

1. Copy the `.savemyass` directory in this repository to the root of your repository.

2. Edit the `_config.json` file in the `.savemyass` directory to specify your repository and the assignment files. The `_config.json` file should look like this:

```json
{
  "instructor_repository": "https://github.com/username/repository",
  "assignments": [
    "path/to/directory/",
    "path/to/file.txt",
    "path/to/another/directory/*.python"
  ]
}
```

Even if enabled, *SaveMyAss* will remain silent for the instructor's repository and will not bother them.

3. **This is an important step!** Add `.savemyass/.secret` to your `.gitignore` file. This file will contain the secret key for encryption and should not be accidentally pushed to the repository.

4. Commit and push the changes to your repository.

5. (Bonus) Add the contents of `INSTRUCTIONS.md` to your repository's `README.md` file to instruct students on how to use *SaveMyAss*.

### For Students

> [!NOTE]
> If the instructor has not provided *SaveMyAss* with the repository, students can add it to their fork using the same steps as above. Here, we assume that the instructor has provided *SaveMyAss* with their repository.

> [!NOTE]
> The following steps assume that you have Python 3.7+ installed on your machine.

1. Fork the instructor's repository.

2. Clone the forked repository to your local machine.

3. Run `python .savemyass/setup.py` from the root of the repository to launch the setup wizard. The setup will ask you to provide the Python command to run on your machine and a secret passkey to encrypt your assignment files. The setup wizard will then automatically install the required git-hooks. If you have previously set up *SaveMyAss* and are cloning the repository again, you must provide the same secret passkey as your previous setup to decrypt the files. The setup wizard will decrypt the files for you.

To uninstall *SaveMyAss* and push the clear text files to your repository, run `python .savemyass/freemyass.py` from the root of the repository. This will remove the git-hooks, decrypt the files, and destroy the secret passkey.

## Contributing and Support
Contributions are most welcome! Please feel free to fork the repository and submit a pull request. If you have any questions or need support with using *SaveMyAss*, please open an issue in the repository.

## Course Repositories using SaveMyAss

- [Proofs and Programs](https://github.com/proofs-and-programs/proofs-and-programs-25), Indian Institute of Science (January 2025)

