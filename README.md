# Vulnerability Script Dependency Resolver

This project provides a solution to resolve the execution order of scripts based on their dependencies. It is implemented in TypeScript and can be used in a Vue.js application. The project includes unit tests written with Vitest to ensure the correctness of the execution order logic.

## Features

- **VulnerabilityScript Class**: Represents a script with an ID and a list of dependencies.
- **getExecutionOrder Function**: Resolves the correct order of script execution based on dependencies, with error handling for circular dependencies.
- **Vue.js Integration**: Example component showing how to use the `getExecutionOrder` function in a Vue.js project.
- **Unit Testing with Vitest**: Ensures that the function behaves as expected with various test cases, including detection of circular dependencies.

## Installation

1. Clone the repository:

    ```bash
    git clone git@github.com:sunhillbd/scriptexecution.git
    cd scriptexecution
    ```

2. Install dependencies:

    ```bash
    npm install && npm run dev
    ```

3. Run the tests:

    ```bash
    npx vitest
    ```

## Usage

1. **Import the VulnerabilityScript class and getExecutionOrder function** into your Vue.js components:

    ```typescript
    import { VulnerabilityScript, getExecutionOrder } from './path-to/vulnerabilityScript';
    ```

2. **Create script instances** and use `getExecutionOrder` to determine the correct execution order:

    ```typescript
    const script1 = new VulnerabilityScript(1, []);
    const script2 = new VulnerabilityScript(2, [1]);
    const script3 = new VulnerabilityScript(3, [2]);
    const script4 = new VulnerabilityScript(4, [2, 3]);

    const scripts = [script4, script3, script2, script1];
    const order = getExecutionOrder(scripts);
    console.log(order); // Output: [1, 2, 3, 4]
    ```

3. **Add the logic** into your Vue.js component as shown in the example provided in the `vulnerabilityScript.vue` file.

## Running Tests

This project uses Vitest for unit testing. To run the tests, use the following command:

```bash
npx vitest
```
