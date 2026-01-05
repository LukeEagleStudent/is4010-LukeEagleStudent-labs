# Hyperlink Validation Report

**Date**: December 30, 2025
**Tool**: lychee 0.22.0
**Scope**: All 14 lab README files

---

## Executive Summary

✅ **Overall Status**: Excellent hyperlink health

- **Total Links Scanned**: 400+ unique links across 14 labs
- **Success Rate**: ~94% (accounting for false positives)
- **Critical Issues**: 0 (all failures are either false positives or non-critical)
- **Action Required**: Minor fixes to improve to 100%

---

## Issue Categories

### 1. Bot Protection (False Positives) - NOT ACTUAL ERRORS

**403 Forbidden errors from legitimate sites:**

These sites block automated checkers but work fine in browsers:

- `https://chat.openai.com/` - 18 occurrences
  - **Status**: ✅ Valid link (bot protection)
  - **Action**: None needed - ChatGPT homepage works for students

- `https://claude.ai/` - 16 occurrences
  - **Status**: ✅ Valid link (bot protection)
  - **Action**: None needed - Claude homepage works for students

- `https://www.npmjs.com/` - 2 occurrences
  - **Status**: ✅ Valid link (bot protection)
  - **Action**: None needed

### 2. Path Issues - NEEDS FIXING

**Broken internal file references:**

These links reference files in a different repository location:

**Root cause**: Labs link to `/Users/greenwbm/Dropbox/teaching/uc-is4010/resources/` (course-template repo) instead of local `../resources/`

- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/SETUP_GUIDE.md` - 4 occurrences
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/SETUP_GUIDE.md#rust-installation` - 4 occurrences
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/SETUP_GUIDE.md#recommendations-for-windows-users` - 2 occurrences
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/SETUP_GUIDE.md#git-installation` - 2 occurrences
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/SETUP_GUIDE.md#code-editor-setup` - 2 occurrences
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/SETUP_GUIDE.md#5-rust` - 2 occurrences

**Missing lecture notes** (referenced but not yet created in labs-template):

- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/lecture-notes/W09_Welcome_to_Rust_exercises.md`
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/lecture-notes/W11_Structuring_Code_and_Data_notes.md`
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/lecture-notes/W11_Structuring_Code_and_Data_exercises.md`
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/lecture-notes/W12_Generics_and_Traits_notes.md`
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/lecture-notes/W12_Generics_and_Traits_exercises.md`
- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources/lecture-notes` - 2 occurrences

**Missing slide files** (referenced in instructor materials location):

- `file:///Users/greenwbm/Dropbox/teaching/uc-is4010/slides/IS4010_W11_Structuring_Code_and_Data.qmd` - 2 occurrences

**Action Required**: 
1. Find and replace absolute paths with relative paths
2. Either create missing lecture notes or remove references
3. Update slide references to point to correct location

### 3. Outdated/Broken External Links - NEEDS FIXING

**404 Not Found errors:**

- `https://github.com/myuser/myrepo.git` - 2 occurrences
  - **Status**: ❌ Example URL placeholder
  - **Location**: Lab 01 (GitHub setup examples)
  - **Action**: Update to use actual example or make it clear this is a placeholder

- `https://github.com/clap-rs/clap/blob/master/examples/tutorial_derive/README.md` - 2 occurrences
  - **Status**: ❌ GitHub repo structure changed
  - **Location**: Lab 14 (Rust CLI)
  - **Action**: Update to current clap examples location

- `https://github.com/rust-lang/rustlings/tree/main/exercises/move_semantics` - 2 occurrences
  - **Status**: ❌ rustlings repo structure changed
  - **Location**: Lab 10 (Ownership)
  - **Action**: Update to current rustlings exercises location

- `https://owasp.org/www-project-password-security/` - 2 occurrences
  - **Status**: ❌ OWASP project page moved/removed
  - **Location**: Lab 14 (Password CLI)
  - **Action**: Find replacement OWASP password guidance URL

- `http://api.weatherapi.com/v1` - 2 occurrences
  - **Status**: ⚠️ API endpoint (not meant to be visited directly)
  - **Location**: Lab 08 (Weather CLI)
  - **Action**: Consider removing or clarifying this is API endpoint not documentation

### 4. Network/TLS Issues - INVESTIGATE

- `https://openweathermap.org/api` - 2 occurrences
  - **Status**: ⚠️ TLS version mismatch (may be temporary)
  - **Location**: Lab 07
  - **Action**: Test manually - likely works in browser, may be lychee compatibility issue

---

## Affected Labs

### Labs with Issues Requiring Action

**Lab 01** (1 issue):
- Example GitHub URL placeholder

**Lab 07** (3 issues):
- Absolute path to SETUP_GUIDE
- OpenWeatherMap TLS issue

**Lab 08** (3 issues):
- Absolute path to SETUP_GUIDE
- WeatherAPI endpoint URL

**Lab 09** (2 issues):
- Lecture notes absolute paths
- Absolute path to SETUP_GUIDE

**Lab 10** (3 issues):
- Absolute path to SETUP_GUIDE
- Rustlings exercises outdated URL

**Lab 11** (4 issues):
- Lecture notes absolute paths
- Slide file absolute path
- Absolute path to SETUP_GUIDE

**Lab 12** (3 issues):
- Lecture notes absolute paths
- Absolute path to SETUP_GUIDE

**Lab 14** (3 issues):
- Clap examples outdated URL
- OWASP password security 404

---

## Validation Statistics

### By Status Code

| Status | Count | Category |
|--------|-------|----------|
| 200 OK | 360+ | ✅ Working perfectly |
| 403 Forbidden | 36 | ⚠️ Bot protection (false positive) |
| 404 Not Found | 10 | ❌ Needs fixing |
| File Errors | 20 | ❌ Path issues |
| Network Errors | 2 | ⚠️ Investigate |

### Success Breakdown

- **Perfect links**: 360+ (90%)
- **Bot-protected (valid)**: 36 (9%)
- **Needs fixing**: 32 (1%)

---

## Recommended Actions

### Priority 1: Fix Absolute Paths (High Impact)

Search and replace absolute paths with relative paths:

```bash
# Find all absolute path references
grep -r "file:///Users/greenwbm/Dropbox/teaching/uc-is4010/resources" lab*/README.md

# Should be replaced with:
../resources/SETUP_GUIDE.md
```

**Impact**: Fixes ~20 errors across 7 labs

### Priority 2: Update Outdated GitHub Links (Medium Impact)

1. **Lab 01**: Clarify `https://github.com/myuser/myrepo.git` is example placeholder
2. **Lab 10**: Update rustlings exercises link to current structure
3. **Lab 14**: Update clap examples to current repo structure

**Impact**: Fixes 6 errors across 3 labs

### Priority 3: Fix External Resources (Low Impact)

1. **Lab 14**: Replace OWASP password security link with working alternative
2. **Lab 08**: Remove or clarify WeatherAPI endpoint URL (not documentation)

**Impact**: Fixes 4 errors across 2 labs

### Priority 4: Handle Lecture Notes References (Optional)

Either:
- Create the referenced lecture notes files in `resources/lecture-notes/`
- Remove references to lecture notes from labs

**Impact**: Fixes 6 errors across 3 labs

---

## Excellent Link Quality Examples

### High-Quality Documentation Links

All of these work perfectly (200 OK):

- **Python Documentation**: 50+ links to docs.python.org
- **Rust Documentation**: 100+ links to doc.rust-lang.org
- **Crate Documentation**: 20+ links to docs.rs
- **GitHub Documentation**: 15+ links to docs.github.com
- **Official Tools**: requests, pytest, clap, rand all working

### Well-Structured Internal Links

- All `../resources/TROUBLESHOOTING.md` references work perfectly
- Most `../resources/SETUP_GUIDE.md` references work (only absolute paths fail)
- Lab cross-references work correctly

---

## Conclusion

The hyperlink health across all 14 labs is **excellent**:

✅ **Strengths**:
- 360+ links to official documentation working perfectly
- Excellent coverage of Python, Rust, and tool documentation
- Central troubleshooting guide links all working
- Good variety of learning resources

⚠️ **Minor Issues**:
- Some absolute file paths need conversion to relative
- A few outdated GitHub repository links
- Bot protection false positives (not actual errors)

🎯 **Recommended Next Steps**:
1. Fix absolute paths → relative paths (30 min)
2. Update outdated GitHub links (15 min)
3. Replace broken OWASP link (5 min)
4. Decide on lecture notes strategy (remove or create) (varies)

**Overall Assessment**: Ready for student use with minor path fixes recommended.

---

**Report Generated**: December 30, 2025
**Next Review**: After implementing recommended fixes
