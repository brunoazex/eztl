# EzTL - Declarative Pipelines Made Simple 🚀

**EzTL** is a **declarative language** designed to simplify the creation, management, and execution of **data pipelines**. With a clean, modular, and extensible syntax, EzTL reduces the complexity of ETL pipelines, enabling you to focus on what matters: turning data into actionable insights.

---

## 🌟 **Why EzTL?**
1. **Simplicity:**
   - Write clear and concise pipelines with the `|>` operator.
   ```etl
   fetch(source: :csv, path: "data.csv")
   |> dropDuplicates(by: "region_id")
   |> filter(col: "value", op: ">=", value: 100)
   |> dispatch(target: :local, path: "output.csv")
   ```

2. **Modularity:**
   - Reuse transformations with native support for modules:
   ```etl
   require my_module::cleanup

   fetch(...)
   |> cleanup
   |> dispatch(...)
   ```

3. **Integrated Testability:**
   - Include tests directly in your pipeline code:
   ```etl
   &test
   mock(fetch: [{ region_id: 1, value: 200 }, { region_id: 2, value: 50 }])
   |> cleanup
   |> assertRowCount(1)
   ```

4. **Runtime Flexibility:**
   - Start locally with a lightweight runtime (Polars) and expand to distributed environments (PySpark and beyond).

---

## 🎯 **Planned Features**
### **MVP**
- **Dummy Runtime (Polars):**
  - Perfect for initial pipeline validation.
- **Intuitive Tooling:**
  - Manage pipelines, runtimes, and plugins effortlessly.
- **Integrated Testing:**
  - Mocks and assertions embedded in pipeline code.
- **Initial Documentation:**
  - Clear and detailed examples and tutorials.

### **Future**
- **PySpark Runtime:**
  - Full support for distributed execution.
- **Morpheus Runtime:**
  - A native runtime designed for high performance and flexibility.
- **Extensibility through Plugins:**
  - Add support for custom sources and targets like Kafka and Snowflake.
- **Advanced Syntax:**
  - Features like `modules` and `&loop` for enhanced control.

---

## 🚀 **How It Works**

### **Simple Pipeline**
```etl
fetch(source: :csv, path: "data.csv")
|> dropDuplicates(by: "region_id")
|> filter(col: "value", op: ">=", value: 100)
|> dispatch(target: :local, path: "output.csv")
```

### **Running with the Dummy Runtime**
1. Add the runtime:
   ```bash
   eztl runtime add dummy-0.1
   ```

2. Execute the pipeline:
   ```bash
   eztl run my_pipeline.ez --on=dummy-0.1
   ```

---

## 🛠 **Tooling**
The EzTL CLI is simple and intuitive:
- **Manage Runtimes:**
  ```bash
  eztl runtime add <runtime>
  eztl runtime list
  eztl runtime global <runtime>
  ```

- **Run Pipelines:**
  ```bash
  eztl run <pipeline>.ez --on=<runtime>
  ```

- **Test Pipelines:**
  ```bash
  eztl test <pipeline>.ez --coverage --output=results.yml
  ```

---

## 📅 **Roadmap**
### **Pre-MVP**
1. **Functional Tooling:** CLI for managing runtimes and pipelines.
2. **Basic Syntax:** Core features like `fetch`, `filter`, and `dispatch`.
3. **Dummy Runtime:** A lightweight runtime based on Polars.

### **MVP**
1. **Complete PoC:** Functional pipeline execution with the dummy runtime.
2. **PySpark Roadmap:** Distributed execution support.
3. **Morpheus Roadmap:** Development of the native runtime.
4. **Extensibility:** Plans for plugins, modules, and advanced syntax.

---

## 🌱 **Contribute to EzTL**
We are just starting, and we’d love your help in shaping the future of EzTL! 🚀

### **How to Contribute?**
1. **Star the Repo ⭐:**
   - Show your support for EzTL by starring this repository.
2. **Test the Pre-MVP:**
   - Run the examples and share your feedback.
3. **Suggest Improvements:**
   - Open issues or contribute with pull requests.

---

## 💬 **Get in Touch**
- **Email:** bcbazevedo@gmail.com

---

Help shape the future of data pipelines. **EzTL** is just getting started, and you can be part of this journey!
