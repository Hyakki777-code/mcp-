# date-tool-mcp

一个基于 [FastMCP](https://github.com/modelcontextprotocol/python-sdk) 的极简 MCP 服务，提供获取当天日期的工具。

## 提供的工具

| 工具 | 说明 | 返回 |
| --- | --- | --- |
| `get_today` | 获取当前年月日 | `YYYY-MM-DD` |

## 安装

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## 运行

默认使用 `stdio` 传输，供 MCP 客户端拉起：

```powershell
python server.py
```

如需以 HTTP 方式调试，可在 `.env` 中把 `FASTMCP_TRANSPORT` 改为 `sse` 或 `streamable-http`，再设置 `FASTMCP_HOST` / `FASTMCP_PORT`。

## 在客户端中配置

`chatmcp.yaml` 已提供 ChatMCP 客户端配置示例：

```yaml
mcpServers:
  date-tool-mcp:
    command: python
    args:
      - D:\PythonProject1\mcpmcp\server.py
    env:
      FASTMCP_LOG_LEVEL: INFO
```

使用 Claude Desktop 等客户端时，把同样的内容转成 JSON 写入 `mcpServers` 字段即可。

## 目录结构

```
mcpmcp/
├── server.py         # MCP 服务入口与工具定义
├── requirements.txt  # Python 依赖
├── chatmcp.yaml      # ChatMCP 客户端配置示例
├── .env              # 运行时环境变量
└── README.md
```
