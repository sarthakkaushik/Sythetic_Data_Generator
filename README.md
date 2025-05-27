# 🧬 Synthetic Data Generator

A comprehensive Python toolkit for generating realistic synthetic data based on JSON table schemas. Automatically preserves statistical distributions, categorical values, and data relationships while ensuring privacy and compliance.

## ✨ Features

- 🎯 **Schema-Driven Generation**: Automatically parses JSON schemas to generate realistic data
- 📊 **Distribution Preservation**: Maintains original categorical distributions and statistical properties
- 🔄 **Multi-Table Support**: Handle multiple related tables with consistent data patterns
- 📁 **Multiple Export Formats**: CSV, JSON, Excel with summary sheets
- ⚡ **Scalable Performance**: Generate from 10 to 100K+ rows efficiently
- 🔍 **Data Validation**: Comprehensive quality checks and schema compliance
- 🛡️ **Privacy-First**: Generate synthetic data that maintains utility without exposing sensitive information

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- UV package manager

### Installation

```bash
# Clone the repository
git clone https://github.com/sarthakkaushik/Sythetic_Data_Generator.git
cd synthetic-data-generator

# Create virtual environment with UV
uv venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
uv add pandas numpy openpyxl
```

### Basic Usage

```python
import json
from synthetic_data_generator import SyntheticDataGenerator

# Load your JSON schema
with open('schemas/your_schema.json', 'r') as f:
    schema = json.load(f)

# Create generator
generator = SyntheticDataGenerator(schema)

# Generate synthetic data
df = generator.generate_synthetic_data(num_rows=1000)

# Export to CSV
df.to_csv('synthetic_data.csv', index=False)
```



## 🔧 Schema Format

Your JSON schema should follow this structure:

```json
{
  "table_name": "your_table_name",
  "columns": {
    "column_name": {
      "data_type": "STRING",
      "nullable": true,
      "is_primary_key": false,
      "categorical_values": ["Value1", "Value2", "Value3"],
      "value_distribution": {
        "Value1": 1000,
        "Value2": 500,
        "Value3": 200
      }
    },
    "numerical_column": {
      "data_type": "INTEGER",
      "nullable": true,
      "is_primary_key": false,
      "numerical_stats": {
        "min_value": 0,
        "max_value": 1000,
        "mean_value": 100,
        "std_dev": 50,
        "null_percentage": 5.0,
        "distinct_count": 150
      }
    }
  }
}
```

## 📚 Usage Examples

### Single Table Generation

```python
from synthetic_data_generator import SyntheticDataGenerator

# Load schema
generator = SyntheticDataGenerator(your_schema)

# Generate data
df = generator.generate_synthetic_data(num_rows=5000)

# Validate quality
stats = generator.get_column_statistics(df)
print(stats)
```



## 🔍 Data Validation

The generator includes comprehensive validation:

```python
# Generate with validation
df = generator.generate_synthetic_data(num_rows=1000, validate_output=True)

# Show validation details
generator.show_validation_details()

# Custom validation
validation_results = generator.validator.validate_dataframe(df, generator.parser)
```

## 📊 Export Options

### CSV Export
```python
from synthetic_data_generator import DataExporter

exporter = DataExporter()
exporter.export_to_csv(df, "synthetic_data.csv")
```

### Excel with Summary
```python
exporter.export_to_excel(df, "synthetic_data.xlsx", include_summary=True)
```

### JSON for APIs
```python
exporter.export_to_json(df, "synthetic_data.json")
```

## 🎯 Use Cases

### Development & Testing
- **Database Testing**: Generate realistic test datasets
- **ETL Pipeline Testing**: Validate data processing workflows
- **Performance Testing**: Create large datasets for load testing
- **API Testing**: Generate JSON data for API endpoints

### Analytics & BI
- **Dashboard Development**: Create realistic data for visualization
- **Report Testing**: Validate report logic with known data patterns
- **ML Model Training**: Generate training data with specific distributions
- **Data Pipeline Validation**: Test data transformation logic

### Compliance & Privacy
- **GDPR Compliance**: Replace sensitive data with synthetic alternatives
- **Data Sharing**: Share realistic datasets without privacy concerns
- **Audit Testing**: Create data for compliance validation
- **Demo Environments**: Populate demo systems with realistic data

## 🔧 Core Features

### Intelligent Data Generation
- ✅ Categorical values use exact schema values only
- ✅ Numerical data respects min/max bounds and distributions
- ✅ Primary keys generate unique identifiers
- ✅ Null values respect nullable constraints
- ✅ Data types match schema specifications

### Business Logic Support
- 🔧 Custom validation rules
- 🔗 Cross-column relationships
- 📅 Time-series data generation
- 🔄 Multi-table referential integrity
- 📊 Industry-specific patterns



## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Setup

```bash
# Clone your fork
git clone https://github.com/yourusername/synthetic-data-generator.git
cd synthetic-data-generator

# Create development environment
uv venv
source .venv/bin/activate

# Install development dependencies
uv add --dev pytest black flake8 mypy pre-commit

# Install pre-commit hooks
pre-commit install
```

## 🔄 Version History

### v1.0.0 (Latest)
- ✨ Initial release
- 🎯 Schema-driven generation
- 📊 Multi-table support
- 💼 Custom business logic
- 📁 Multiple export formats
- 🔍 Comprehensive validation

### Upcoming Features
- 🔗 Advanced cross-table relationships
- ⏰ Time-series pattern recognition
- 🌍 Geographic data support
- 🤖 ML model integration
- 📊 Advanced statistical distributions


## 🙏 Acknowledgments

- Built for data professionals and developers
- Designed for privacy-first synthetic data generation
- Optimized for large-scale data generation
- Focused on maintaining statistical utility


## 🚀 Quick Examples

### Generate Sample Data
```python
# Quick 10-row sample
sample_df = generator.generate_sample_data(sample_size=10)
print(sample_df.head())
```

### Validate Schema Compliance
```python
# Check if generated data matches schema
validation = generator.validator.validate_dataframe(df, generator.parser)
print(f"Validation passed: {validation['is_valid']}")
```

### Export Data Dictionary
```python
# Create documentation
exporter.create_data_dictionary(generator.parser, "data_dictionary.xlsx")
```



⭐ **Star this repository** if you find it helpful!

🔔 **Watch** for updates and new features!

🍴 **Fork** to contribute or customize for your needs!