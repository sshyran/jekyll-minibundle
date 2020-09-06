# Releasing

1. Check that [CI] is green.

2. Double check that tests pass:

    ``` shell
    BUNDLE_GEMFILE=Gemfile-jekyll4 bundle exec rake
    BUNDLE_GEMFILE=Gemfile-jekyll3 bundle exec rake
    ```

3. Update `Jekyll::Minibundle::VERSION`:

    ``` shell
    $EDITOR lib/jekyll/minibundle/version.rb
    ```

4. Summarize changes since the last release:

    ``` shell
    $EDITOR CHANGELOG.md
    ```

5. Review your changes, commit them, tag the release:

    ``` shell
    git diff
    git add -p
    git commit -m 'Release version $version'
    git tag v$version
    ```

6. Build the gem, push commits and tags, publish the gem:

    ``` shell
    BUNDLE_GEMFILE=Gemfile-jekyll4 bundle exec rake gem:build
    git push origin master v$version
    gem push jekyll-minibundle-$version.gem
    ```

[CI]: https://github.com/tkareine/jekyll-minibundle/actions?workflow=CI
