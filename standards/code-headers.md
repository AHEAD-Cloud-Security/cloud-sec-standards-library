# Code Headers & Disclaimers

> Standardized file headers for lab/demo content with clear usage warnings and approval requirements.

## Purpose

These headers ensure that lab and demo content is clearly marked as non-production and requires proper validation before deployment to client environments.

## Header Templates

### Terraform (.tf)

```hcl
# =============================================================================
# WARNING: Lab/Demo Content - Not Production Ready
# =============================================================================
# This infrastructure is intentionally designed for security training,
# vulnerability testing, and educational purposes only.
#
# USAGE RESTRICTIONS:
# - For lab, demo, or reference use only
# - Must be validated, tested, and approved before production deployment
# - Remove this header after formal security review and approval
# - Never deploy to production subscriptions with real data
#
# SECURITY CONSIDERATIONS:
# - Contains intentional misconfigurations for training purposes
# - Uses minimal security controls for educational value
# - May expose sensitive data or access patterns
#
# APPROVAL REQUIRED:
# - Security team review and approval
# - Client acceptance of risk
# - Production hardening and testing
# =============================================================================

# Terraform configuration begins here...
```

### Python (.py)

```python
"""
 =============================================================================
 WARNING: Lab/Demo Content - Not Production Ready
 =============================================================================
 This code is intentionally designed for security training,
 vulnerability testing, and educational purposes only.
 
 USAGE RESTRICTIONS:
 - For lab, demo, or reference use only
 - Must be validated, tested, and approved before production deployment
 - Remove this header after formal security review and approval
 - Never deploy to production environments with real data
 
 SECURITY CONSIDERATIONS:
 - Contains intentional vulnerabilities for training purposes
 - Uses minimal security controls for educational value
 - May expose sensitive data or access patterns
 
 APPROVAL REQUIRED:
 - Security team review and approval
 - Client acceptance of risk
 - Production hardening and testing
 =============================================================================
"""

# Python code begins here...
```

### PowerShell (.ps1)

```powershell
<#
 =============================================================================
 WARNING: Lab/Demo Content - Not Production Ready
 =============================================================================
 This script is intentionally designed for security training,
 vulnerability testing, and educational purposes only.
 
 USAGE RESTRICTIONS:
 - For lab, demo, or reference use only
 - Must be validated, tested, and approved before production deployment
 - Remove this header after formal security review and approval
 - Never deploy to production environments with real data
 
 SECURITY CONSIDERATIONS:
 - Contains intentional vulnerabilities for training purposes
 - Uses minimal security controls for educational value
 - May expose sensitive data or access patterns
 
 APPROVAL REQUIRED:
 - Security team review and approval
 - Client acceptance of risk
 - Production hardening and testing
 =============================================================================
#>

# PowerShell code begins here...
```

### TypeScript/JavaScript (.ts/.js)

```typescript
/**
 =============================================================================
 WARNING: Lab/Demo Content - Not Production Ready
 =============================================================================
 This code is intentionally designed for security training,
 vulnerability testing, and educational purposes only.
 
 USAGE RESTRICTIONS:
 - For lab, demo, or reference use only
 - Must be validated, tested, and approved before production deployment
 - Remove this header after formal security review and approval
 - Never deploy to production environments with real data
 
 SECURITY CONSIDERATIONS:
 - Contains intentional vulnerabilities for training purposes
 - Uses minimal security controls for educational value
 - May expose sensitive data or access patterns
 
 APPROVAL REQUIRED:
 - Security team review and approval
 - Client acceptance of risk
 - Production hardening and testing
 =============================================================================
 */

// TypeScript/JavaScript code begins here...
```

### YAML (.yml/.yaml)

```yaml
# =============================================================================
# WARNING: Lab/Demo Content - Not Production Ready
# =============================================================================
# This configuration is intentionally designed for security training,
# vulnerability testing, and educational purposes only.
#
# USAGE RESTRICTIONS:
# - For lab, demo, or reference use only
# - Must be validated, tested, and approved before production deployment
# - Remove this header after formal security review and approval
# - Never deploy to production environments with real data
#
# SECURITY CONSIDERATIONS:
# - Contains intentional misconfigurations for training purposes
# - Uses minimal security controls for educational value
# - May expose sensitive data or access patterns
#
# APPROVAL REQUIRED:
# - Security team review and approval
# - Client acceptance of risk
# - Production hardening and testing
# =============================================================================

# YAML configuration begins here...
```

### Bash/Shell (.sh)

```bash
#!/bin/bash
# =============================================================================
# WARNING: Lab/Demo Content - Not Production Ready
# =============================================================================
# This script is intentionally designed for security training,
# vulnerability testing, and educational purposes only.
#
# USAGE RESTRICTIONS:
# - For lab, demo, or reference use only
# - Must be validated, tested, and approved before production deployment
# - Remove this header after formal security review and approval
# - Never deploy to production environments with real data
#
# SECURITY CONSIDERATIONS:
# - Contains intentional vulnerabilities for training purposes
# - Uses minimal security controls for educational value
# - May expose sensitive data or access patterns
#
# APPROVAL REQUIRED:
# - Security team review and approval
# - Client acceptance of risk
# - Production hardening and testing
# =============================================================================

# Shell script begins here...
```

## Implementation Guidelines

### When to Use Headers

**Required for:**
- All lab and demo environment code
- Intentionally vulnerable configurations
- Educational security examples
- Reference implementations for clients

**Not Required for:**
- Production-ready code after approval
- Infrastructure as code modules (use module-level documentation)
- Standard utility scripts and tools
- Documentation files

### Header Removal Process

1. **Security Review**: Complete formal security assessment
2. **Client Approval**: Obtain written client acceptance
3. **Production Hardening**: Apply all required security controls
4. **Testing**: Validate in production-like environment
5. **Documentation**: Update with production deployment guide
6. **Remove Header**: Delete warning header from approved code

### Automated Detection

Consider implementing automated checks to:

- Scan for missing headers in lab repositories
- Flag production deployments with lab headers
- Validate header format and content
- Track approval status and lifecycle

## Integration with Development Workflows

### Pre-commit Hooks

```bash
#!/bin/bash
# Check for required headers in lab files
check_headers() {
    local file="$1"
    case "$file" in
        *.tf)
            if ! grep -q "WARNING: Lab/Demo Content" "$file"; then
                echo "Missing lab header in $file"
                return 1
            fi
            ;;
        *.py|*.ps1|*.ts|*.js|*.sh|*.yml|*.yaml)
            if ! grep -q "WARNING: Lab/Demo Content" "$file"; then
                echo "Missing lab header in $file"
                return 1
            fi
            ;;
    esac
    return 0
}
```

### GitHub Actions

```yaml
name: Check Lab Headers
on: [push, pull_request]
jobs:
  check-headers:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Check for required headers
        run: |
          find . -type f \( -name "*.tf" -o -name "*.py" -o -name "*.ps1" \) | while read file; do
            if ! grep -q "WARNING: Lab/Demo Content" "$file"; then
              echo "Missing lab header: $file"
              exit 1
            fi
          done
```

## Customization Guidelines

### Client-Specific Headers

Modify headers to include:
- Client name and project identifier
- Specific security requirements
- Custom approval workflows
- Client contact information

### Environment-Specific Headers

Create variations for:
- Development environments
- Staging/testing environments
- Production environments (after approval)

## Compliance Considerations

### Regulatory Requirements

Ensure headers address:
- SOX compliance for financial institutions
- HIPAA requirements for healthcare
- PCI DSS for payment processing
- Industry-specific regulations

### Audit Trail

Maintain records of:
- Header removal approvals
- Security review dates
- Client acceptance documentation
- Production deployment timestamps

---

**Usage**: Apply these headers consistently across all lab and demo content to ensure clear usage boundaries and proper approval processes.
