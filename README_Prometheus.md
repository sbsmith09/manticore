# Manticore: A Lightweight Python Static Site Generator

## Project Overview

Manticore is a lightweight and minimalist static site generator designed to simplify the process of creating websites from markdown content. It provides an easy-to-use solution for developers and content creators who want to generate static websites with minimal configuration.

### Key Features

- **Simple Markdown-based Content Creation**: Write content easily using markdown files in the `content` directory
- **Multiple Template Support**: 
  - Blog template generation
  - Resume template generation
- **Flexible Command-Line Interface**: Generate sites with simple command-line options
- **Minimal Dependencies**: Leverages lightweight Python libraries for parsing and rendering
- **Responsive Design**: Utilizes Skeleton CSS and Normalize CSS for mobile-friendly layouts

### Primary Use Cases

- Personal blogs
- Professional resume websites
- Simple, fast-loading static websites
- Quick content publishing without complex CMS systems

The generator converts markdown files into static HTML pages using Jinja2 templating, making it an ideal solution for developers and writers seeking a straightforward way to create and manage web content.

## Getting Started, Installation, and Setup

### Prerequisites

- Python 3.6 or higher
- pip package manager

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/manticore.git
   cd manticore
   ```

2. Create and activate a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### Quick Start

#### Blog Generation
1. Add markdown files to the `content/default` directory
2. Generate the blog site:
   ```bash
   python build.py --default default
   ```
3. The generated site will be in the `output/posts` directory

#### Resume Generation
1. Add a markdown file to the `content/resume` directory
2. Generate the resume site:
   ```bash
   python build.py --resume resume
   ```
3. The generated site will be in the `output` directory

### Development

- To view available commands:
  ```bash
  python build.py --help
  ```

### Project Structure
```
manticore/
│
├── content/
│   ├── default/      # Blog post markdown files
│   └── resume/       # Resume markdown files
│
├── templates/        # HTML templates
│   ├── default/
│   └── resume/
│
├── build.py          # Main build script
├── parse.py          # Content parsing
├── render.py         # Template rendering
└── requirements.txt  # Project dependencies
```

### Notes
- The project uses Jinja2 for templating
- Markdown files are converted to HTML using markdown2
- Generated sites are static HTML files

## Usage

The tool is a static site generator that can create HTML templates for blogs and resumes from Markdown files.

### Basic Usage

Generate site files by running the script with appropriate flags:

```bash
python build.py --default
python build.py --resume
```

### Command Options

- `--default` or `-d`: Generate the default blog template
  - Parses Markdown files from `content/default/`
  - Renders blog posts as HTML
  - Outputs files in the `output/` directory

- `--resume` or `-r`: Generate a resume template
  - Parses Markdown file from `content/resume/resume.md`
  - Renders resume details as an HTML page
  - Outputs file as `output/resume.html`

### Example Workflow

#### Blog Generation
1. Place your blog post Markdown files in `content/default/`
   - Each file should have metadata like title, date, blog, and slug
2. Run the command:
   ```bash
   python build.py --default
   ```
3. Check generated files in the `output/` directory:
   - `home.html`: Index of all blog posts
   - `posts/[slug].html`: Individual blog post pages

#### Resume Generation
1. Prepare your resume details in `content/resume/resume.md`
   - Include metadata like name, designation, address, etc.
2. Run the command:
   ```bash
   python build.py --resume
   ```
3. Find the generated resume at `output/resume.html`

### Output

After running either command, you'll see a logging message:
- `Build successful. Check your output folder.` (if generation is successful)
- An error message if something goes wrong

### Notes
- Ensure all required Markdown files exist before generation
- Generated files will overwrite existing files in the `output/` directory

## Command Reference

The project uses Click for command-line interface management. Here are the available commands and options:

### Build Commands

| Command | Options | Description | Example |
|---------|---------|-------------|---------|
| `python build.py` | `--default` or `-d` | Generate the default blog template | `python build.py --default` |
| `python build.py` | `--resume` or `-r` | Generate a resume template | `python build.py --resume` |

#### Command Options

- `--default` / `-d`: 
  - Parses markdown files from `content/default/` directory
  - Generates blog posts and a home page
  - Creates HTML files in the `output/` directory
  - Posts are sorted by date in descending order

- `--resume` / `-r`:
  - Parses the resume markdown file from `content/resume/resume.md`
  - Generates a resume HTML page
  - Creates `output/resume.html`

### Execution Notes

- Exactly one option (`--default` or `--resume`) should be used per build command
- Logs will be displayed in the console indicating build success or failure
- Output files are generated in the `output/` directory

## Configuration

### Content Configuration

The project uses Markdown files for content configuration, with specific metadata requirements:

#### Blog Posts
Blog posts are located in `content/default/` directory and require the following metadata in the Markdown file:
- `title`: The title of the blog post
- `blog`: Blog post description
- `date`: Publication date (format: `DD Mon YYYY`, e.g., `15 Jan 2023`)
- `slug`: URL-friendly identifier for the post

Example blog post metadata:
```markdown
---
title: My First Blog Post
blog: An introduction to my writing
date: 15 Jan 2023
slug: first-blog-post
---

Post content here...
```

#### Resume Configuration
The resume configuration is located in `content/resume/resume.md` and requires the following metadata:
- `name`: Full name
- `designation`: Professional title
- `address`: Postal address
- `phone`: Contact phone number
- `email`: Contact email address

Example resume metadata:
```markdown
---
name: John Doe
designation: Software Engineer
address: 123 Tech Lane, Coding City
phone: +1 (555) 123-4567
email: john.doe@example.com
---

Resume content here...
```

### Template Configuration
The project uses Jinja2 templates located in the `templates/` directory:
- `templates/default/`: Templates for blog posts
  - `home.html`: Homepage template
  - `post.html`: Individual post template
- `templates/resume/`: Templates for resume
  - `home.html`: Resume page template
- `templates/layout.html`: Base layout template

### Output Configuration
Generated HTML files are automatically created in the `output/` directory:
- `output/home.html`: Generated homepage
- `output/posts/`: Directory containing individual post HTML files
- `output/resume.html`: Generated resume page

## Project Structure

The project is organized into several key directories and files to support content generation and rendering:

### Directory Structure
- `content/`: Contains source markdown files for different content types
  - `content/default/`: Stores blog post markdown files
    - `article.md`
    - `newarticle.md`
  - `content/resume/`: Contains resume-related markdown file
    - `resume.md`

- `templates/`: Holds HTML templates for rendering content
  - `templates/default/`: Templates for default blog posts
    - `home.html`
    - `post.html`
  - `templates/resume/`: Resume-specific templates
    - `home.html`
  - `layout.html`: Base layout template

### Key Python Files
- `build.py`: Main build script with command-line interface for generating content
- `parse.py`: Handles parsing of markdown files for blog posts and resume
- `render.py`: Manages the rendering of parsed content into HTML

### Supporting Files
- `requirements.txt`: Lists project dependencies
- `LICENSE`: Project licensing information
- `.gitignore`: Specifies intentionally untracked files to ignore
- `.gitattributes`: Defines attributes for repository files

## Technologies Used

### Programming Language
- Python 3

### Core Libraries and Frameworks
- [Click](https://click.palletsprojects.com/) (v7.1.1): Command-line interface creation kit
- [Jinja2](https://jinja.palletsprojects.com/) (v2.11.3): Template engine for Python
- [markdown2](https://github.com/trentm/python-markdown2) (v2.3.8): Markdown parser and converter
- [MarkupSafe](https://markupsafe.palletsprojects.com/) (v1.1.1): HTML template escaping library

### Development Tools
- Git: Version control system
- Markdown: Content writing and documentation

### Project Structure Tools
- os: Python standard library for operating system interactions
- pathlib: Python standard library for filesystem path operations
- datetime: Python standard library for date and time manipulation

### Rendering and Parsing
- Environment: Jinja2 template environment for dynamic HTML generation
- Markdown parsing with metadata extraction

### File Handling
- JSON-like metadata parsing
- HTML file generation
- Markdown file processing

## Additional Notes

### Performance and Efficiency
The static site generator is designed to be lightweight and quick, leveraging Python's efficient libraries like Markdown2 and Jinja2 for parsing and templating.

### Supported Content Types
- Blog posts (markdown files in `content/default`)
- Resume/Personal page (markdown files in `content/resume`)

### Limitations and Considerations
- Currently supports only markdown-based content
- Limited to two template types (blog and resume)
- Requires manual file management in content directories

### Troubleshooting
- Ensure Python 3.6+ is installed
- Check that all required dependencies are installed via `requirements.txt`
- Verify markdown files are correctly formatted
- Confirm template files exist in the `templates` directory

### Future Roadmap
- Implement custom category and tag support
- Develop additional static site templates (portfolio, landing page)
- Explore advanced deployment options
- Enhance template customization capabilities

### Known Issues
- Deployment methods are currently limited
- No automatic content validation
- Minimal error handling in build process

### Security Considerations
- Always validate and sanitize markdown content before rendering
- Use caution when adding external templates or plugins

## Contributing

We welcome contributions to Manticore! Whether you're fixing bugs, adding features, or improving documentation, your help is appreciated.

### Ways to Contribute

- Report bugs by opening GitHub issues
- Suggest new features or improvements
- Submit pull requests with bug fixes or enhancements

### Contribution Guidelines

#### Prerequisites
- Python 3.6 or higher
- Basic understanding of Python and static site generation

#### Setup for Development
1. Fork the repository
2. Create a virtual environment
3. Install dependencies: `pip install -r requirements.txt`

#### Development Process
- Ensure your code follows Python best practices
- Write clear, concise commit messages
- Include tests for new functionality
- Update documentation when necessary

#### Dependencies
The project currently uses the following key libraries:
- Click (CLI interface)
- Jinja2 (Templating)
- markdown2 (Markdown processing)

#### Reporting Issues
- Use GitHub Issues to report bugs
- Provide a clear description of the issue
- Include steps to reproduce, expected behavior, and actual behavior
- If possible, include a minimal code example

#### Pull Request Process
1. Ensure your code passes all existing tests
2. Update the README or documentation with details of changes
3. Your pull request will be reviewed by the maintainers

#### Code of Conduct
- Be respectful and inclusive
- Collaborate constructively
- Focus on the quality of contributions

## License

This project is licensed under the MIT License. 

For the full license text, please see the [LICENSE](LICENSE) file in the repository.

#### Key Permissions
- Commercial use
- Modification
- Distribution
- Private use

#### Conditions
- License and copyright notice must be included
- The software is provided "as is" without warranties

#### Limitations
- Limited liability
- No trademark rights