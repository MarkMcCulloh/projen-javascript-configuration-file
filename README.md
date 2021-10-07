# Javascript config file component for projen

WIP and subject to change

## Assumptions

- 

## Usage


*Note: End a line with `//!` to remove it from the final output*


**In projenrc:**
```typescript
import { Configuration } from "webpack";

const projectName = project.name;
new JavascriptConfigComponent<Configuration>(
    project,
    "webpack.config.mjs",
    (webpackEnv) => {
      console.log("test"); //!
      return {
        name: projectName,
      };
    },
    {
      imports: [
        {
          module: "webpack-merge",
          nameImports: ["merge"],
        },
      ],
      variables: {
        projectName,
      },
    }
  );
```

**Resulting `webpack.config.mjs`**

```javascript
import { merge } from "webpack-merge";
const projectName = "test-project";

export default () => {
    return {
        name: projectName,
    };
};
```