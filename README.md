# 文档处理服务器 Atlas Docs

Atlas Docs MCP服务器为AI助手提供库和框架的技术文档，将官方文档处理为适合LLM使用的Markdown版本，适用于Cursor、Cline、Windsurf等MCP兼容的LLM客户端。
The Atlas Docs MCP server provides technical documentation of libraries and frameworks for AI assistants, processes the official documentation into Markdown versions suitable for LLMS, and is applicable to McP-compatible LLM clients such as Cursor, Cline, Windsurf, etc.## 工具列表 Tool List

本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。 本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。

| 工具 Tool   | 描述 Description         |
|-------|--------------------|
| list_docs | Lists all available documentation libraries and frameworks. Use this as your first step to discover available documentation sets. Returns name, description and source url for each documentation set. Required before using other documentation tools since you need the docName. |
| search_docs | Searches a documentation set for specific content. Use this to find pages containing particular keywords, concepts, or topics. Returns matching pages ranked by relevance with their paths and descriptions. Follow up with get_docs_page to get full content. |
| get_docs_index | Retrieves a condensed, LLM-friendly index of the pages in a documentation set. Use this for initial exploration to understand what's covered and identify relevant pages. Returns a markdown page with a list of available pages. Follow up with get_docs_page to get full content. |
| get_docs_page | Retrieves a specific documentation page's content using its relative path. Use this to get detailed information about a known topic, after identifying the relevant page through get_docs_index or search_docs. Returns the complete content of a single documentation page. |
| get_docs_full | Retrieves the complete documentation content in a single consolidated file. Use this when you need comprehensive knowledge or need to analyze the full documentation context. Returns a large volume of text - consider using get_docs_page or search_docs for targeted information. |


## 检查服务 ## Inspector

工具在线测试： [https://mcp.xiaobenyang.com/inspector/1777316659387395](https://mcp.xiaobenyang.com/inspector/1777316659387395)

Online Tool test [https://mcp.xiaobenyang.com/inspector/1777316659387395](https://mcp.xiaobenyang.com/inspector/1777316659387395)

## 服务配置 MCP Server Config


> #### 如何获取 XBY-APIKEY ？ How to get XBY-APIKEY ?
> 访问小笨羊科技网站 [https://xiaobenyang.com](https://xiaobenyang.com)，注册用户即可获得APIKEY
> Visit XiaoBenYang website [https://xiaobenyang.com](https://xiaobenyang.com), register and get the APIKEY.

### SSE
```json
{
  "mcpServers": {
    "文档处理服务器": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "sse",
      "url": "https://mcp.xiaobenyang.com/1777316659387395/sse"
    }
  }
}
```
### STREAMABLE HTTP
```json
{
  "mcpServers": {
    "文档处理服务器": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "streamable_http",
      "url": "https://mcp.xiaobenyang.com/1777316659387395/mcp"
    }
  }
}
```
### STDIO
```json
{
    "mcpServers": {
        "文档处理服务器": {
          "command": "npx",
          "args": [
            "-y",
            "xiaobenyang-mcp"
          ],
          "env": {
            "XBY_APIKEY": "<YOUR_XBY_APIKEY>",
            "mcpId": "1777316659387395",
          },
          "transport": "stdio"
        }
      }
}

```
