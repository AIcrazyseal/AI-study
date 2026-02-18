#  Equipping agents for the real world with Agent Skills
```
Anthropic发布
20256.2.16
```

**技术思路：通用Agent+Skill（有序的指令skill.md、脚本scripts、references文件、assets模板打包成可组合、专业知识的资源）=垂直领域专用Agent。**\
**优势：一个通用Agent、动态发现并渐进式加载不同专业领域的Skill文件夹，完成特定专业领域任务,从而实现完成跨域复杂任务，避免开发定制的专业领域Agent。** \
![Agent + Skills + Virtual Machine](../../images/Agent+Skills+VirtualMachine.png)

## skill文件结构
